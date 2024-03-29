<!--
 FileName:      ros2
 Author:        8ucchiman
 CreatedDate:   2023-06-06 12:18:51
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     8ucchiman.jp
 Description:   ---
-->


- Tutorials
    - [Beginner: CLI tools](#Beginner-CLI-tools)
        - Configure environment
        - Using turtlesim, ros2, and rqt
        - Understanding nodes
        - Understanding topics
        - Understanding services
        - Understanding parameters
        - Understanding actions
        - Using rqt_console to view logs
        - Launching nodes
        Recording and playing back data
    - Beginner: Client libraries
        - Using colcon to build packages
        - Creating a workspace
        - Creating a package
        - Writing a simple publisher and subscriber (C++)
        - Writing a simple publisher and subscriber (python)
        - Writing a simple service and client (C++)
        - Writing a simple service and client (python)
        - Creating custom msg and srv files
        - Implementing custom interfaces
        - Using parameters in a class (C++)
        - Using parameters in a class (python)
        - Using ros2doctor to identify issues
        - Creating and using plugins (C++)
    - Intermediate
    - Advanced
    - Demos
    - Miscellaneous


# Tutorials
## Beginner: CLI tools
<details>
<summary>Beginner: CLI tools</summary>
 <div>

 ## Understanding nodes <br />
  ![Nodes-TopicandService](https://github.com/Bucchiman/readme/assets/52972710/364045e8-c84d-4ec9-89d2-0c79521b5134) <br />
 ## Understanding topics <br />
  ![Topic-MultiplePublisherandMultipleSubscriber](https://github.com/Bucchiman/readme/assets/52972710/c0eb35d1-f8a4-47a9-8584-cfd9074e4a27) <br />
 ## Understanding services <br />
  ![Service-MultipleServiceClient](https://github.com/Bucchiman/readme/assets/52972710/aa765780-905d-4fb5-af2e-a09ab8daad0f) <br />
 ## Understanding parameters <br />
 ## Understanding actions <br />
  ![Action-SingleActionClient](https://github.com/Bucchiman/readme/assets/52972710/72bd0938-0094-451b-a605-ae503dce417f) <br />
 ## Launching nodes
 </div>
</details>

<details>
<summary>Beginner:Client libraries</summary>
## Using parameters in a class(C++)

 ### Background
 When making your own nodes you will sometimes need to add parameters that can be set from the launch file. <br />
 This tutorial will show you how to create those parameters in a c++ class, and how to set them in a launch file.

## Using ros2doctor to identify issues
### Background
 When your ROS2 setup is not running as expected, you can check its settings with the `ros2doctor` tool. <br />
 `ros2doctor` checks all aspects of ROS 2, including platform, version, network, environment, running systems and more, and warns you about possible errors and reasons for issues.
## Creating and using plugins(C++)
 This tutorial is derived from [https://wiki.ros.org/pluginlib](https://wiki.ros.org/pluginlib) and [Writing and Using a Simple Plugin Tutorial](http://wiki.ros.org/pluginlib/Tutorials/Writing%20and%20Using%20a%20Simple%20Plugin) <br />
 pluginlib is a C++ library for loading and unloading plugins from within a ROS package. Plugins are dynamically loadable classes that are loaded from a runtime library(i.e. shared object, dynamically linked library).
 With pluginlib, one does not have to explicitly link their application against the library containing the classes -
 instead pluginlib can open a library containing exported classes at any point without the application having any prior awareness of the library or the header file containing the class definition.
 Plugins are useful for extending/modifying application behavior without needing the application source code.

</details>
<details>
 <summary>Intermediate</summary>
## Managing Dependencies with rosdep
### What is rosdep?
 依存管理コマンド。colconはビルドするだけで依存関係まで解決しない。
 rosdepはpackage.xmlから依存関係のチェックをする。

### What is `package.xml`?
依存関係に関するファイル。
- \<depend\>
- \<test_depend\> ... `gtest`
- \<exec_depend\>
- \<build_depend\>
- \<build_export_depend\>

## Creating an action
### Background


## Writing an action server and client(C++)
## Composing multiple nodes in a single process
## Monitoring for parameter changes(C++)
## Launch
## tf2
## Testing
## URDF
</details>
<details>
 <summary>Advanced</summary>
</details>
<details>
 <summary>Demos</summary>
</details>
<details>
 <summary>Miscellaneous</summary>
</details>
