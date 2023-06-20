<!-- 
 FileName:      readme
 Author:        8ucchiman
 CreatedDate:   2023-02-26 20:41:00 +0900
 LastModified:  2023-03-08 19:24:49 +0900
 Reference:     https://docs.nvidia.com/cuda/pdf/CUDA_C_Programming_Guide.pdf
                https://docs.nvidia.com/cuda/cuda-runtime-api/modules.html#modules
                https://www.nvidia.com/content/gtc/documents/1055_gtc09.pdf
                https://www.nvidia.co.jp/docs/IO/59373/VolumeI.pdf
-->


- 1. Introduction
    - 1.1 
- 2. Programming Model
    - 2.1 Kernels
    - 2.2 Thread Hierarchy
        - 2.2.1 Thread Block Clusters
    - 2.3 Memory Hierarchy
    - 2.4 Heterogeneous Programming
    - 2.5 Asynchronous SIMT Programming Model
        - 2.5.1 Asynchronous Operations
    - 2.6 Compute Capability
- 3. Programming Interface
    - 3.1 Compilation with NVCC
    - 3.2 CUDA Runtime
    - 3.3 Versioning and Compatibility
    - 3.4 Compute Modes
    - 3.5 Mode Switches
    - 3.6 Tesla Compute Cluster Mode for Windows
- 4. Hardware Implementation
    - 4.1 SIMT Architecture
    - 4.2 Hardware Multithreading
- 5. Performance Guidelines
    - 5.1 Overall Performance Optimization Strategies
    - 5.2 Maximize Utilization
        - 5.2.1 Application Level
        - 5.2.2 Device Level
        - 5.2.3 Multiprocessor Level
            - 5.2.3.1 Occupancy Calculator
    - 5.3 Maximize Memory Throughput
        - 5.3.1 Data Transfer between Host and Device
        - 5.3.2 Device Memory Accesses
    - 5.4 Maximize Instruction Throughput
        - 5.4.1 Arithmetic Instructions
        - 5.4.2 Control Flow Instructions
        - 5.4.3 Synchronization Instructions
        - 5.4.4 Minimize Memory Thrashing
- 6. CUDA-Enabled GPUs
- 7. C++ Language Extentions
    - 7.1 Function Execution Space Specifiers
        - 7.1.1 __global__
        - 7.1.2 __device__
        - 7.1.3 __host__
        - 7.1.4 Undefined behavior
        - 7.1.5 __noinline__ and __forceline__
    - 7.2 Variable Memory Space Specifiers
        - 7.2.1 __device__
        - 7.2.2 __constant__
        - 7.2.3 __shared__
        - 7.2.4 __grid_constant__
        - 7.2.5 __managed__
        - 7.2.6 __restrict__
    - 7.3 Built-in Vector Types
        - 7.3.1 char, short, int, long, longlong, float, double
        - 7.3.2 dim3
    - 7.4 Built-in Variables
        - 7.4.1 gridDim
        - 7.4.2 blockIdx
        - 7.4.3 blockDim
        - 7.4.4 threadIdx
        - 7.4.5 warpSize
    - 7.5 Memory Fence Functions
    - 7.6 Synchronization Functions
    - 7.7 Mathematical Functions
    - 7.8 Texture Functions
        - 7.8.1 Texture Object API
    - 7.9 Surface Functions
    - 7.10 Read-Only Data Cache Load Function
    - 7.11 Load Functions Using Cache Hints
    - 7.12 Store Functions Using Cache Hints
    - 7.13 Time Functions
    - 7.14 Atomic Functions
    - 7.15 Address Space Predicate Functions
    - 7.16 Address Space Conversion Functions
    - 7.17 Alloca Function
    - 7.18 Compiler Optimization Hint Functions
- 8. Cooperative Groups
- 9. CUDA Dynamic Parallelism
- 10. Virtual Memory Management
- 11. Stream Ordered Memory Allocator
- 12. Graph Memory Nodes
- 13. Mathematical Functions
- 14. C++ Language Support
- 15. Texture Fetching
- 16. Compute Capabilities
- 17. Driver API
- 18. CUDA Environment Variables
- 19. Unified Memory Programming
- 20. Lazy Loading


# 2. Programming


# 関数の修飾子

関数の宣言に修飾子をつけてkernel関数(deviceで実行される関数)とhost関数を区別する

 - __global__

hostから呼び出されてdeviceで実行される

返り値なし

 - __device__

deviceから呼び出されてdeviceで実行

再帰関数不可

 - __host__

hostから呼び出されてhostで実行

## __global__
`hostから呼び出し、device実行`
修飾子省略可
```cuda
    // Kernel関数宣言
    __global__ void mykernel(float* arguments) {
    }

    int main(void) {
        // ホスト側でdevice関数呼び出し
        mykernel <<<Dg, Db>>> (arguments); # <<<Dg, Db>>>はthread数の指定
    }
```

各スレッドは、kernel関数内の同じ命令を実行するが、扱うデータが異なる(SIMD: Single Instruction Multiple Data)

## threadの定義
kernel関数はスレッド単位で並列に実行される
```cuda
    <<<Dg, Db>>> grid, thread
```

```cuda
    dim3 Dg(xdiv, ydiv, zdiv);
    dim3 Db(xdiv, ydiv, zdiv);
    mykernel <<<Dg, Db>>>();
```

```cuda
    dim3 Dg(1, 2, 1);
    dim3 Db(4, 4, 1);
    #
    # +=============
    # =+----+-----+=
    # =-////--////-=
    # =-////--////-=
    # =-////--////-=
    # =+----++----+=
    # +=============
    #
    # +=============
    # =+----+-----+=
    # =-////--////-=
    # =-////--////-=
    # =-////--////-=
    # =+----++----+=
    # +=============
    #
    # =: grid
    # -: block
    # /: thread
```

# CPU/GPU間のデータ転送
# デバイスメモリの確保
`cudaMalloc: デバイスメモリ確保`
```cuda
    cudaError_t cudaMalloc(void** devptr, size_t count)
    // devptr: デバイスメモリのアドレスのポインタ
    // count:  領域のサイズ
```

```cuda
    double* dev;
    cudaMalloc((void**)&dev, sizeof(double)*512)
```

## データ転送
```cuda
    cudaError_t cudaMemcpy(void* dat, const void* src, size_t count, enum cudaMemcpyKind kind)
    // dat: 転送先のアドレス
    // src: 転送元のアドレス
    // count: 領域のサイズ
    // kind: 転送サイズを指定する定数
    //     cudaMemcpyHostToDevice(host memoryからdevice memoryへ)
    //     cudaMemcpyDeviceToHost(device memoryからhost memoryへ)
    //     cudaMemcpyDeviceToDevice(device memoryからdevice memoryへ)
```

```cuda
    cudaMemcpy(dev, host, sizeof(double)*512, cudaMemcpyHostToDevice);
```

## デバイスメモリ解放
```cuda
    cudaError_t cudaFree(void* devptr)
    // devptr: デバイスメモリのアドレスのポインタ
```



# thread index

```cuda
    # grid内のblockのDim定義
    gridDim.x = 2
    gridDim.y = 3
    # block内のthreadのDim定義
    blockDim.x = 6
    blockDim.y = 4

    #    +================+
    #         0       1
    #    =+------+-------+=
    #      012345  012345
    #   0=-//////--//////-=
    # 0 1=-//////--//////-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    =+------++------+=
    #   0=-//////--//////-=
    # 1 1=-//////--//////-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    =+------++------+=
    #   0=-//////--//////-=
    # 2 1=-//////--//////-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    +================+

    threadIdx.x = 2
    threadIdx.y = 1
    blockIdx.x = 1
    blockIdx.y = 1

    #    +================+
    #         0       1
    #    =+------+-------+=
    #      012345  012345
    #   0=-//////--//////-=
    # 0 1=-//////--//////-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    =+------++------+=
    #   0=-//////--//////-=
    # 1 1=-//////--//*///-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    =+------++------+=
    #   0=-//////--//////-=
    # 2 1=-//////--//////-=
    #   2=-//////--//////-=
    #   3=-//////--//////-=
    #    =+------++------+=
    #    +================+
    #
    # =: grid
    # -: block
    # /: thread

```


# the basis of the programming in CUDA

```cuda
    __global__ void mykernel() {

    }

    int main() {
        - hostメモリ宣言    
             float* h_A;
             nBytes = 512*sizeof(float);
        - hostメモリ確保
             h_A = (float*) malloc(nBytes);
        - deviceメモリ宣言
             float* d_A;
        - deviceメモリ確保
             cudaMalloc((float**)&d_A, nBytes);
        - hostメモリからdeviceメモリにデータ転送
             cudaMemcpy(d_A, h_A, nBytes, cudaMemcpyHostToDevice);
        - スレッド数の宣言
             dim3 block(512);
             dim3 grid(512);
        - カーネル関数の呼び出し
             mykernel<<<grid, block>>>(d_A);
        - 同期処理
             cudaDeviceSynchronize();
        - deviceメモリからhostメモリにデータ転送
             cudaMemcpy(h_A, d_A, nBytes, cudaMemcpyDeviceToHost);
        - hostメモリの解放
             free(h_A);
        - deviceメモリの解放
             cudaFree(d_A);
             return 0;
    }
```

# バリア同期関数
 - __syncthreads()

    block単位で同期をとる。kernel関数上で実行

 - cudaDeviceSynchronize()
    全スレッドに対し同期をとる。host関数上で実行


# GPU Architecture

```
    *---------------------------*
    |SM    *----* *----*        |
    | //// | CC | | CC | ...    |
    | //// *----* *----*        |
    | /RM/    |      |          |
    | //// *----------------*   |
    | //// | shared memory  |   |
    |      |  e.g. l1 chache|   |
    |      *----------------*   |
    *---------------------------*
    SM: Streaming Multiprocessor
    RM: レジスタメモリ
    CC: CUDA Core

    *-----* *-----* *-----* *-----*
    | SM  | | SM  | | SM  | | SM  | ...
    *-----* *-----* *-----* *-----*
       |       |       |       |
    *---------------------------------*
    |                                 |
    |         デバイスメモリ          |
    |                                 |
    *---------------------------------*

```

# CUDA memory model
```
                        size     access speed
    レジスタメモリ       ^             v
    シェアードメモリ     ^             v
    コンスタントメモリ   ^             v
    テクスチャメモリ     ^             v
    グローバルメモリ     ^             v
```
```
    *SM---------------------------*
    | *-------------------------* |
    | | SP(Streaming Processor) | |
    | *-------------------------* |
    | *RM-----------------------* |
    |    |                        |
    | *shared memory|L1 cache---* |
    |    |                        |
    | *L2 cache--*                |
    |    | *constant cache--*     |
    |    |      | *texture cache-*|
    |    |      |        |        |
    *----+------+--------+--------*
         |      |        |
    *----+------+--------+--------*
    |    |      |        |        |
    |    |      | *texture memory*|
    |    | *constant memory--*    |
    |*global memory--*            |
    *Device Memory----------------*

```

## global memory
`cuda mallocによってグローバルメモリ確保`
cudaMallocではグローバルメモリに確保される
```cuda
    #include <stdio.h>

    __global__ void mykernel(double* array) {
    }

    int main() {
        cudaMalloc((void**) array, sizeof(double)*512);
    }
```

## shared memory
`ブロック内で確保できるメモリ`
ブロック内で共有できるメモリ
```cuda
    #include <stdio.h>

    __global__ void mykernel(double* array) {
        __shared__ int array[512];   # __shared__変数修飾子
        extern __shared__ char hoge[]; # 動的確保の場合
    }

    int main() {
        mykernel <<<Dg, Db, Ns>>>();
    }
```


# Warp Divergent
GPUでは複数のthreadがwarpという一つの単位で動く
通常は1warp=32threads固定である

warp divergent: 条件分岐によりwarp内で異なる処理が行われた場合、すべての分岐先の処理が逐次的に実行される

warp内の分岐を極力減らす

# Coalescing
global memoryにアクセスするときhalf warp(16threads)でアクセスする。
これをcoalescingと呼ぶ。
coalescing accessによって高速化できる。
```
    e.g.  coalescing access
    *-threads-*   *-global memory-*
    |  a   b  |   | a b / / / / / |
    |  c   d  |   | c d / / / / / |
    *---------*   | / / / / / / / |
                  *---------------*

          no coalescing access
                  *-global memory-*
                  | / / a / / / / |
                  | c / / / b / / |
                  | / / / / / / d |
                  *---------------*
```
## coalescingが働く条件
- 16threadsのアクセスするアドレスが隣接している
- 先頭アドレスが64 or 128 byte境界に位置する

```
       th01 th02 th03 ...
         |    |    |
       *--------------------------------------
       |128  132  136  140  144  148  152  ...
       *--------------------------------------
            ------------------------------------------------*
            ...  156  160  164  168  172  176  180  184  188|
            ------------------------------------------------*

```
- アクセスしないthreadがあってもよい
```
       th01 th02 th03 th04 th05 th06 th07
         |         |    |              |
       *--------------------------------------
       |128  132  136  140  144  148  152  ...
       *--------------------------------------
            ------------------------------------------------*
            ...  156  160  164  168  172  176  180  184  188|
            ------------------------------------------------*

```

- アクセスの順番はばらばらでよい
```
       th01 th02 th03 th04 th05 th06 th07
         |      /         \            
       *--------------------------------------
       |128  132  136  140  144  148  152  ...
       *--------------------------------------
            ------------------------------------------------*
            ...  156  160  164  168  172  176  180  184  188|
            ------------------------------------------------*

```


# cuda profiler

 |       項目      |                       Description                            |
 |-----------------|--------------------------------------------------------------|
 |timestamp        | タイムスタンプ                                               |
 |gridsize         | グリッドのブロック数                                         |
 |threadblocksize  | ブロック当たりのスレッド数                                   |
 |dynsmemperblock  | 動的に確保したシェアードメモリ                               |
 |stasmemperblock  | 静的に確保したシェアードメモリ                               |
 |regperthread     | 各スレッドの使用レジスタ数                                   |
 |memtransferdir   | 転送の方向
 |memtransfersize  | 転送データ・サイズ
 |streamid         | ストリーム番号
 |gId incoherent   | コアレッシングされなかったグローバルメモリからの読み込み回数
 |gId coherent     | コアレッシングされたグローバルメモリからの読み込み回数
 |gId 32b          | 32バイト単位で行われたグローバルメモリからの読み込み回数
 |gId 64b          | 64バイト単位で行われたグローバルメモリからの読み込み回数
 |gId 128b         | 128バイト単位で行われたグローバルメモリからの読み込み回数
 |gId request      | グローバルメモリからの読み込み回数
 |gst incoherent   | コアレッシングされなかったグローバルメモリへの書き込み回数
 |gst coherent     | コアレッシングされたグローバルメモリへの書き込み回数
 |gst 32b          | 32バイト単位で行われたグローバルメモリへの書き込み回数
 |gst 64b          | 64バイト単位で行われたグローバルメモリへの書き込み回数
 |gst 128b         | 128バイト単位で行われたグローバルメモリへの書き込み回数
 |gst request      | グローバルメモリへの書き込み回数
 |local load       | ローカルメモリからの読み込み回数
 |local store      | ローカルメモリへの書き込み回数
 |branch           | 分岐命令の数
 |divergent branch | 分岐命令でwarpが分断した回数
 |instruction      | 実行した命令数
 |warp serializatio|
 |cta launcher     |


# thread, block, grid hierarchy
[概要](https://developer.nvidia.com/blog/cuda-refresher-cuda-programming-model/)
thread, block, gridとGPUの対応関係

```
    CUDA thread              CUDA core
        /          ->            ||

    -.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.

    CUDA block               CUDA streaming Multiprocessor(SM)
    +--------+                   +************+
    -////////-     ->            *|| || || || *
    +--------+                   +************+

    -.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.

    CUDA grid                CUDA-capble GPU
    +--------+               +************+
    -////////-               *|| || || || *
    +--------+               +************+
                   ->
    +--------+               +************+
    -////////-               *|| || || || *
    +--------+               +************+

    -.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.-.
```

# Memory Hierarchy
```

  +--SM0----------------------+ +--SM1----------------------+ +--SM2----------------------+
  |+-Registers---------------+| |+-Registers---------------+| |+-Registers---------------+|
  ||256kb per SM in A100     || ||256kb per SM in A100     || ||256kb per SM in A100     ||
  |+-------------------------+| |+-------------------------+| |+-------------------------+|
  |+L1/SMEM------+ +Read-Only+| |+L1/SMEM------+ +Read-Only+| |+L1/SMEM------+ +Read-Only+|
  ||192kb in A100| |         || ||192kb in A100| |         || ||192kb in A100| |         ||
  |+-------------+ +---------+| |+-------------+ +---------+| |+-------------+ +---------+|
  +---------------------------+ +---------------------------+ +---------------------------+

  +---L2 Cache----------------------------------------------------------------------------+
  |     40mb in a100                                                                      |
  +---------------------------------------------------------------------------------------+

  +---Global Memory-----------------------------------------------------------------------+
  |     DRAM 40GB in A100                                                                 |
  +---------------------------------------------------------------------------------------+

```

- Registers

 お互いのthreadは干渉することはない(データ共有など)

- L1/Shared memory(SMEM)

 ブロック内の全てのthreadはShared Memoryにて共有できる

- Read only memory
- L2 cache

どのブロックのどのthreadも共有できる


# インデックス
[概要](https://www.nvidia.co.jp/docs/IO/59373/VolumeI.pdf)

- threadIdx.x ブロック内のスレッドID
- blockIdx.x  グリッド内のブロックID
- blockDim.x  ブロック当たりのスレッドの数

```
                                   +===========================+
blockIdx.x                         =+b0-----++b1-----++b2-----+=
blockDim.x=4                       =-/ / / /--/ / / /--/ / / /-=
threadIdx.x                        =+0-1-2-3++0-1-2-3++0-1-2-3+=
                                   +===========================+

blockIdx.x*blockDim.x+threadIdx.x    0 1 2 3  4 5 6 7  8 91011

=: grid
-: block
/: thread

```
