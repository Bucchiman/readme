<!--
 FileName:      README
 Author:        8ucchiman
 CreatedDate:   2023-04-23 16:14:42
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://www.lua.org/pil/contents.html#P1
 Description:   ---
-->

# Part I · The Language
- [1. Getting Started](https://www.lua.org/pil/1.html)
    - [1.1 Chunks](#11-Chunks)
    - [1.2 Global Variables](#12-Global-Variables)
    - [1.3 Some Lexical Conventions](#13-SOme-Lexical-Conventions)
    - [1.4 The Stand-Alone Interpreter](#14-The-Stand-Alone-Interpreter)
- [2. Types and Values](https://www.lua.org/pil/2.html)
    - [2.1 Nil](#21-Nil)
    - [2.2 Booleans](#22-Booleans)
    - [2.3 Numbers](#23-Numbers)
    - [2.4 Strings](#24-Strings)
    - [2.5 Tables](#25-Tables)
    - [2.6 Functions](#26-Functions)
    - [2.7 Userdata and Threads](#27-Userdata-and-Threads)
- [3. Expressions](https://www.lua.org/pil/3.html)
    - [3.1 Arithmetic Operators](#31-Arighmetic-Operators)
    - [3.2 Relational Operators](#32-Relational-Operators)
    - [3.3 Logical Operators](#33-Logical-Operators)
    - [3.4 Concatenation](#34-Concatenation)
    - [3.5 Precedence](#35-Precedence)
    - [3.6 Table Constructors](#36-Table-Constructors)
- [4. Statements](https://www.lua.org/pil/4.html)
    - [4.1 Assignment](#41-Assignment)
    - [4.2 Local Variables and Blocks](#42-Local-Variables-and-Blocks)
    - [4.3 Control Structures](#43-Control-Structures)
        - [4.3.1 if then else](#431-if-then-else)
        - [4.3.2 while](#432-while)
        - [4.3.3 repeat](#433-repeat)
        - [4.3.4 Numeric for](#434-Numeric-for)
        - [4.3.5 Generic for](#435-Generic-for)
    - [4.4 break and return](#44-break-and-return)
- [5. Functions](https://www.lua.org/pil/5.html)
    - [5.1 Multiple Results](#51-Multiple-Results)
    - [5.2 Variable Number of Arguments](#52-Variable-Number-of-Arguments)
    - [5.3 Named Arguments](#53-Named-Arguments)
- [6. More about Functions](https://www.lua.org/pil/6.html)
    - [6.1 Closures](#61-Closures)
    - [6.2 Non-Global Functions](#62-Non-Global-Functions)
    - [6.3 Proper Tail Calls](#63-Proper-Tail-Calls)
- [7. Iterators and the Generic for](https://www.lua.org/pil/7.html)
    - [7.1 Iterators and Closures](#71-Iterators-and-Closures)
    - [7.2 The Semantics of the Generic for](#72-The-Semantics-of-the-Generic-for)
    - [7.3 Stateless Iterators](#73-Stateless-Iterators)
    - [7.4 Iterators with Complex State](#74-Iterators-with-Complex-State)
    - [7.5 True Iterators](#75-True-Iterators)
- [8. Compilation, Execution, and Errors](https://www.lua.org/pil/8.html)
    - [8.1 The require Function](#81-The-require-Funcion)
    - [8.2 C Packages](#82-C-Packages)
    - [8.3 Errors](#83-Errors)
    - [8.4 Error Handling and Exceptions](#84-Error-Handling-and-Exceptions)
    - [8.5 Error Messages and Tracebacks](#85-Error-Messages-and-Tracebacks)
- [9. Coroutines](https://www.lua.org/pil/9.html)
    - [9.1 Coroutine Basics](#91-Coroutine-Basics)
    - [9.2 Pipes and Filters](#92-Pipes-and-Filters)
    - [9.3 Coroutines as Iterators](#93-Coroutines-as-Iterators)
    - [9.4 Non-Preemptive Multithreading](#94-Non-Preem)
- [10. Complete Examples](https://www.lua.org/pil/10.html)
    - [10.1 Data Description](#101-Data-Description)
    - [10.2 Markov Chain Algorithm](#102-Markov-Chain-Algorithm)

# Part II · Tables and Objects
- [11. Data Structures](https://www.lua.org/pil/11.html)
    - [11.1 Arrays](#111-Arrays)
    - [11.2 Matrices and Multi-Dimensional Arrays](#112-Matrices-and-Multi-Dimensional-Arrays)
    - [11.3 Linked Lists](#113-Linked-Lists)
    - [11.4 Queues and Double Queues](#114-Queues-and-Double-Queues)
    - [11.5 Sets and Bags](#115-Sets-and-Bags)
    - [11.6 String Buffers](#116-String-Buffers)
- [12. Data Files and Persistence](https://www.lua.org/pil/11.html)
    - [12.1 Serialization](121-Serialization)
        - [12.1.1 Saving Tables without Cycles](#12110-Saving-Tables-without-Cycles)
        - [12.1.2 Saving Tables with Cycles](#1212-Saving-Tables-with-Cycles)
- [13. Metatables and Metamethods](https://www.lua.org/pil/11.html)
    - [13.1 Arithmetic Metamethods](#131-Arithmetic-Metamethods)
    - [13.2 Relational Metamethods](#132-Relational-Metamethods)
    - [13.3 Library-Defined Metamethods](#133-Library-Defined-Metamethods)
    - [13.4 Table-Access Metamethods](#134-Table-Access-Metamethods)
        - [13.4.1 The \_\_index Metamethod](#1341-The-__index-Metamethod)
        - [13.4.2 The \_\_newindex Metamethod](#1342-The-__newindex-Metamethod)
        - [13.4.3 Tables with Default Values](#1343-Tables-with-Default-Values)
        - [13.4.4 Tracking Table Accesses](#1344-Tracking-Table-Accesses)
        - [13.4.5 Read-Only Tables](#1345-Read-Only-Tables)
- [14. The Environment](https://www.lua.org/pil/11.html)
    - [14.1 Accessing Global Variables with Dynamic Names](#141-Accessing-Global-Variables-with-Dynamic-Names)
    - [14.2 Declaring Global Variables](#142-Declaring-Global-Variables)
    - [14.3 Non-Global Environments](#143-Non-Global-Environments)
- [15. Packages](https://www.lua.org/pil/11.html)
    - [15.1 The Basic Approach](#151-The-Basic-Approach)
    - [15.2 Privacy](#152-Privacy)
    - [15.3 Packages and Files](#153-Packages-and-Files)
    - [15.4 Using the Global Table](#154-Using-the-Global-Table)
    - [15.5 Other Facilities](#155-Other-Facilities)
- [16. Object-Oriented Programming](https://www.lua.org/pil/11.html)
    - [16.1 Classes](#161-Classes)
    - [16.2 Inheritance](#162-Inheritance)
    - [16.3 Multiple Inheritance](#163-Multiple-Inheritance)
    - [16.4 Privacy](#164-Privacy)
    - [16.5 The Single-Method Approach](#165-The-Single-Method-Approach)
- [17. Weak Tables](https://www.lua.org/pil/17.html)
    - [17.1 Memoize Functions](#171-Memorize-Functions)
    - [17.2 Object Attributes](#172-Object-Attributes)
    - [17.3 Revisiting Tables with Default Values](#173-Revisiting-Tables-with-Default-Values)

# Part III · The Standard Libraries
- [18. The Mathematical Library](https://www.lua.org/pil/11.html)
- [19. The Table Library](https://www.lua.org/pil/11.html)
    - [19.1 Array Size](#191-Array-Size)
    - [19.2 Insert and Remove](#192-Insert-and-Remove)
    - [19.3 Sort](#193-Sort)
- [20. The String Library](https://www.lua.org/pil/11.html)
    - [20.1 Pattern-Matching Functions](#201-Pattern-Matcing-Functions)
    - [20.2 Patterns](#202-Patterns)
    - [20.3 Captures](#203-Captures)
    - [20.4 Tricks of the Trade](#204-Tricks-of-the-Trade)
- [21. The I/O Library](https://www.lua.org/pil/11.html)
    - [21.1 The Simple I/O Model](#211-The-Simple-I/O-Model)
    - [21.2 The Complete I/O Model](#212-The-Complete-I/O-Model)
        - [21.2.1 A Small Performance Trick](#2121-A-Small-Performance-Tric)
        - [21.2.2 Binary Files](#2122-Binary-Files)
    - [21.3 Other Operations on Files](#213-Other-Operations-on-Files)
- [22. The Operating System Library](https://www.lua.org/pil/11.html)
    - [22.1 Date and Time](#221-Data-and-Time)
    - [22.2 Other System Calls](#222-Other-System-Calls)
- [23. The Debug Library](https://www.lua.org/pil/11.html)
    - [23.1 Introspective Facilities](#231-Introspective-Facilities)
        - [23.1.1 Accessing Local Variables](#2311-Accessing-Local-Variables)
        - [23.1.2 Accessing Upvalues](#2312-Accessing-Upvalues)
    - [23.2 Hooks](#232-Hooks)
    - [23.3 Profiles](#233-Profiles)

# Part IV · The C API
- [24. An Overview of the C API](https://www.lua.org/pil/24.html)
    - [24.1 A First Example](#241-A-First-Example)
    - [24.2 The Stack](#242-The-Stack)
        - [24.2.1 Pushing Elements](#2421-Pushing-Elements)
        - [24.2.2 Querying Elements](#2422-Querying-Elements)
        - [24.2.3 Other Stack Operations](#2423-Other-Stack-Operations)
    - [24.3 Error Handling with the C API](#243-Error-Handling-with-the-C-API)
        - [24.3.1 Error Handling in Application Code](#2431-Error-Handling-in-Application-Code)
        - [24.3.2 Error Handling in Library Code](#2432-Error-Handling-in-Library-Code)
- [25. Extending your Application](https://www.lua.org/pil/25.html)
    - [25.1 Table Manipulation](#251-Table-Manipulation)
    - [25.2 Calling Lua Functions](#252-Calling-Lua-Functions)
    - [25.3 A Generic Call Function](#253-A-Generic-Call-Function)
- [26. Calling C from Lua](https://www.lua.org/pil/26.html)
    - [26.1 C Functions](#261-C-Functions)
    - [26.2 C Libraries](#262-C-Libraries)
- [27. Techniques for Writing C Functions](https://www.lua.org/pil/27.html)
    - [27.1 Array Manipulation](#271-Array-Manipulation)
    - [27.2 String Manipulation](#272-String-Manipulation)
    - [27.3 Storing State in C Functions](#273-Storing-State-in-C-Functions)
        - [27.3.1 The Registry](#2731-The-Registry)
        - [27.3.2 References](#2732-References)
        - [27.3.3 Upvalues](#2733-Upvalues)
- [28. User-Defined Types in C](https://www.lua.org/pil/28.html)
    - [28.1 Userdata](#281-Userdata)
    - [28.2 Metatables](#282-Metatables)
    - [28.3 Object-Oriented Access](#283-Object-Oriented-Access)
    - [28.4 Array Access](#284-Array-Access)
    - [28.5 Light Userdata](#285-Light-Userdata)
- [29. Managing Resources](https://www.lua.org/pil/29.html)
    - [29.1 A Directory Iterator](#291-A-Directory-Iterator)
    - [29.2 An XML Parser](#292-An-XML-Parser)

# [1. Getting Started](https://www.lua.org/pil/1.html)
## 1.1 Chunks
## 1.2 Global Variables
## 1.3 Some Lexical Conventions
## 1.4 The Stand-Alone Interpreter

# [2. Types and Values](https://www.lua.org/pil/2.html)
## 2.1 Nil
## 2.2 Booleans
## 2.3 Numbers
## 2.4 Strings
## 2.5 Tables
## 2.6 Functions
## 2.7 Userdata and Threads

# [3. Expressions](https://www.lua.org/pil/3.html)
## 3.1 Arithmetic Operators
## 3.2 Relational Operators
## 3.3 Logical Operators
## 3.4 Concatenation
## 3.5 Precedence
## 3.6 Table Constructors

# [4. Statements](https://www.lua.org/pil/4.html)
## 4.1 Assignment
`Assignment is the basic means of changing the value of a variable or a table field` <br />
- e.g.
```lua
    a = "hello" .. "world"
    t.n = t.n + 1
```

- e.g.
```lua
    a, b = 10, 2*x
```

- e.g.
```lua
    x, y = y, x    -- swap x for y
    a[i], a[j] = a[j], a[i]
```

- e.g.
```lua
    a, b, c = 0, 1
    print(a, b, c)    -- 0 1 nil
    a, b = a+1, b+1, b+2  -- value of b+2 is ignored
    print(a, b)       -- 1 2
    a, b, c = 0
    print(a, b, c)    -- 0, nil, nil
```

## 4.2 Local Variables and Blocks
- e.g.
```lua
    j = 10          -- global variable
    local i = 1     -- local variable
```
## 4.3 Control Structures
- if
- while
- repeat
- for
- break and return

### 4.3.1 if then else
### 4.3.2 while
```lua
    local i = 1
    while a[i] do
        print(a[i])
        i = i + 1
    end
```
### 4.3.3 repeat
```lua
    repeat
        line = io.read()
    until line ~= ""
    print(line)
```

### 4.3.4 Numeric for
- e.g.
```lua
    for var = exp1, exp2, exp3 do
        something
    end
```

- e.g.
```lua
    for i=1, f(x) do print(i) end
    for i=10, 1, -1 do print(i) end
```

- e.g.
```lua
    local found = nil
    for i=1, a.n do
        if a[i] == value then
            found = 1
            break
        end
    end
    print(found)
```

### 4.3.5 Generic for
```lua
    for i, v in ipairs(a) do print(v) end
```

```lua
    for k in pairs(t) do print(k) end
```

## 4.4 break and return

# [5. Functions](https://www.lua.org/pil/5.html)
## 5.1 Multiple Results
## 5.2 Variable Number of Arguments
## 5.3 Named Arguments

# [6. More about Functions](https://www.lua.org/pil/6.html)
```lua
    a = {a = print}
    a.p("Hello World") --> Hello World
    print = math.sin   -- 'print' now refers to the sing function
    a.p(print(1))
    sin = a.p          -- 'sin' now refers to the print function
    sin(10, 20)        --> 10 20
```
## 6.1 Closures
- [参照](https://nishi2.info/pydp/GoF_dp/other/python_class_is_first-class_object.html) <br />
```lua
    names = {"Peter", "Paul", "Mary"}
    grades = {Mary = 10, Paul = 7, Peter = 8}
    table.sort(names, function (n1, n2)
        return grades[n1] > grades[n2]
    end)

    -->
    function sortbygrade (names, grades)
        table.sort(names, function (n1, n2)
            return grades[n1] > grades[n2]   -- compare the grades
        end)                                 -- 関数内関数
    end
```

```lua
    function newCounter ()
        local i = 0
        return function ()
            i = i+1
            return i
        end
    end

    c1 = newCounter()
    print(c1())  --> 1
    print(c1())  --> 2

    c2 = newCounter()
    print(c2())  --> 1
    print(c1())  --> 3
    print(c2())  --> 2
```


## 6.2 Non-Global Functions
## 6.3 Proper Tail Calls

# [7. Iterators and the Generic for](https://www.lua.org/pil/7.html)
## 7.1 Iterators and Closures
## 7.2 The Semantics of the Generic for
## 7.3 Stateless Iterators
## 7.4 Iterators with Complex State
## 7.5 True Iterators

# [8. Compilation, Execution, and Errors](https://www.lua.org/pil/8.html)
## 8.1 The require Function
## 8.2 C Packages
## 8.3 Errors
## 8.4 Error Handling and Exceptions
## 8.5 Error Messages and Tracebacks

# [9. Coroutines](https://www.lua.org/pil/9.html)
## 9.1 Coroutine Basics
## 9.2 Pipes and Filters
## 9.3 Coroutines as Iterators
## 9.4 Non-Preemptive Multithreading

# [10. Complete Examples](https://www.lua.org/pil/10.html)
## 10.1 Data Description
## 10.2 Markov Chain Algorithm

# Part II · Tables and Objects
# [11. Data Structures](https://www.lua.org/pil/11.html)
## 11.1 Arrays
## 11.2 Matrices and Multi-Dimensional Arrays
## 11.3 Linked Lists
## 11.4 Queues and Double Queues
## 11.5 Sets and Bags
## 11.6 String Buffers
# [12. Data Files and Persistence](https://www.lua.org/pil/12.html)
## 12.1 Serialization
### 12.1.1 Saving Tables without Cycles
### 12.1.2 Saving Tables with Cycles
# [13. Metatables and Metamethods](https://www.lua.org/pil/13.html)
```lua
    t = {}
    print(getmetatable(t))     --> nil

    t1 = {}
    setmetatable(t, t1)
    assert(getmetatable(t) == t1)
```
## 13.1 Arithmetic Metamethods
```lua
    Set = {}

    function Set.new (t)
        local set = {}
        for _, l in ipairs(t) do set[l] = true end
            return set
    end

    function Set.union(a, b)
        local res = Set.new{}
        for k in pairs(a) do res[k]
    end
```
## 13.2 Relational Metamethods
## 13.3 Library-Defined Metamethods
## 13.4 Table-Access Metamethods
### 13.4.1 The __index Metamethod
### 13.4.2 The __newindex Metamethod
### 13.4.3 Tables with Default Values
### 13.4.4 Tracking Table Accesses
### 13.4.5 Read-Only Tables
# [14. The Environment](https://www.lua.org/pil/14.html)
## 14.1 Accessing Global Variables with Dynamic Names
## 14.2 Declaring Global Variables
## 14.3 Non-Global Environments

# [15. Packages](https://www.lua.org/pil/15.html)
## 15.1 The Basic Approach
## 15.2 Privacy
## 15.3 Packages and Files
## 15.4 Using the Global Table
## 15.5 Other Facilities

# [16. Object-Oriented Programming](https://www.lua.org/pil/16.html)
## 16.1 Classes
## 16.2 Inheritance
## 16.3 Multiple Inheritance
## 16.4 Privacy
## 16.5 The Single-Method Approach

# [17. Weak Tables](https://www.lua.org/pil/17.html)
## 17.1 Memoize Functions
## 17.2 Object Attributes
## 17.3 Revisiting Tables with Default Values

# Part III · The Standard Libraries
# 18. The Mathematical Library
# 19. The Table Library
## 19.1 Array Size
## 19.2 Insert and Remove
## 19.3 Sort

# 20. The String Library
## 20.1 Pattern-Matching Functions
## 20.2 Patterns
## 20.3 Captures
## 20.4 Tricks of the Trade

# 21. The I/O Library
## 21.1 The Simple I/O Model
## 21.2 The Complete I/O Model
### 21.2.1 A Small Performance Trick
### 21.2.2 Binary Files
## 21.3 – Other Operations on Files
# 22. The Operating System Library
## 22.1 Date and Time
## 22.2 Other System Calls
# 23. The Debug Library
## 23.1 Introspective Facilities
### 23.1.1 Accessing Local Variables
### 23.1.2 Accessing Upvalues
## 23.2 Hooks
## 23.3 Profiles

# Part IV · The C API
# 24. An Overview of the C API
## 24.1 A First Example
## 24.2 The Stack
### 24.2.1 Pushing Elements
### 24.2.2 Querying Elements
### 24.2.3 Other Stack Operations
## 24.3 Error Handling with the C API
### 24.3.1 Error Handling in Application Code
### 24.3.2 Error Handling in Library Code

# 25. Extending your Application
## 25.1 Table Manipulation
## 25.2 Calling Lua Functions
## 25.3 A Generic Call Function

# 26. Calling C from Lua
## 26.1 C Functions
## 26.2 C Libraries

# 27. Techniques for Writing C Functions
## 27.1 Array Manipulation
## 27.2 String Manipulation
## 27.3 Storing State in C Functions
### 27.3.1 The Registry
### 27.3.2 References
### 27.3.3 Upvalues
# 28. User-Defined Types in C
## 28.1 Userdata
## 28.2 Metatables
## 28.3 Object-Oriented Access
## 28.4 Array Access
## 28.5 Light Userdata
# 29. Managing Resources
## 29.1 A Directory Iterator
## 29.2 An XML Parser

