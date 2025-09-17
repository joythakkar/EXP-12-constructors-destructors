#Joy Thakkar
# Experiment 12: Constructors and Destructors in C++

## Aim
- To understand the concept of **constructors** and **destructors** in C++.
- To explore different **types of constructors**: default, parameterized, and copy constructors.
- To differentiate between constructors and destructors in terms of working and purpose.

---

## Tools Used
- Language: C++
- Compiler/IDE: VS Code

---

## Objectives
- To define and use constructors for automatic initialization of objects.
- To implement multiple types of constructors in a class.
- To use method overloading with constructors.
- To study destructors and their role in cleanup.
- To compare constructors and destructors for better understanding.

---

## Theory

## Constructors
- A **constructor** is a special member function in C++ used to initialize objects when they are created.
- The name of a constructor is the **same as the class name**.
- It is called **automatically** at the time of object creation.
- It does not return any value (not even `void`).
- Helps in achieving better code readability and ensures that an object always starts in a valid state.
- Constructors may include default arguments, which provide flexibility in initialization.

### Syntax
```cpp
class ClassName {
public:
    ClassName() {
        // constructor body
    }
};
```
--- 

## Types of Constructors in C++
### Default Constructor
-  Takes **no arguments**.
-  Automatically assigns **predefined values** to the attributes.
-  Useful when no specific initialization values are provided.
-  If no constructor is defined, the compiler provides a default one.

** Basic Algorithm : **
1. Define a class with attributes.
2. Create a constructor with the same name as the class and no parameters.
3. Assign default values to attributes inside the constructor.
4. Instantiate the object → attributes will automatically hold the default values.

---

### Parameterized Constructor
- Takes **arguments from the user**.
-  Used to initialize attributes with **user-defined or dynamic values**.
-  Allows flexibility by passing values at the time of object creation.
-  Can also include **default parameters** for optional arguments.

** Basic Algorithm : **
1. Define a class with attributes.
2. Create a constructor with parameters.
3. Assign the passed arguments to the attributes.
4. Instantiate the object → pass values as arguments → attributes will be initialized with user-defined values.

---

### Copy Constructor
- Used to **initialize one object using another existing object**.
- Takes a **reference to another object of the same class** as a parameter.
- Invoked when:
  - An object is initialized from another of the same type.
  - An object is passed by value to a function.
  - An object is returned from a function.

** Basic Algorithm : **
1. Define a class with attributes.
2. Create a constructor that accepts a reference to another object of the same class.
3. Copy the values of attributes from the passed object into the new one.
4. Instantiate a new object using an already existing object → values will be copied automatically.

---


## Difference Between Types of Constructors

| Feature             | Default Constructor                                  | Parameterized Constructor                               | Copy Constructor                                   |
|---------------------|------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|
| **Arguments**       | None                                                 | Yes (user-defined values)                              | One object reference                             |
| **Purpose**         | Assigns default / fixed values to data members        | Initializes attributes with values provided by user     | Initializes an object using values of another    |
| **Definition**      | Constructor with no parameters                       | Constructor with one or more parameters                | Constructor with a reference to same class object|
| **Invocation**      | Automatic when object is created without arguments   | Automatic when arguments are passed at creation         | Automatic when object is copied, passed, or returned |
| **Flexibility**     | Least flexible (values are fixed)                    | Most flexible (can take multiple and varied inputs)     | Special purpose only                             |
| **User Control**    | No control over initialization values                | Full control over initialization                       | No control, just replicates existing object      |
| **Reusability**     | Low – always assigns same values                     | High – can be reused for multiple initializations       | Medium – reuses existing object’s data           |
| **Example Use Case**| Initializing counters, IDs, or flags to zero/NULL     | Initializing objects like BankAccount(name, balance)    | Duplicating objects like copying Student records |
| **Default Provided?**| Provided by compiler if not explicitly defined       | Must be explicitly defined by programmer               | Provided by compiler unless overridden           |
| **Performance**     | Fast, minimal overhead                               | Slight overhead due to parameter passing                | Slight overhead due to copying operation         |
| **Overloading**     | Cannot be overloaded (only one default constructor)  | Can be overloaded with multiple parameter lists         | Not overloaded, but can be user-defined          |

---

## Destructors

- A **destructor** is a special member function in C++ that destroys objects when they go out of scope.  
- Its name is the same as the class name, but prefixed with a tilde `(~)`.  
- Destructors are **automatically invoked** when:
  1. An object goes out of scope.  
  2. The `delete` operator is called for dynamically allocated objects.  
- Main purposes of destructors:
  - Release dynamically allocated memory.  
  - Close file handles.  
  - Free network connections.  
  - Perform cleanup tasks before object destruction.  
- Rules about destructors:
  - Cannot be overloaded.  
  - Cannot have parameters or a return type.  
  - Each class can have only **one destructor**.  

### Syntax:
```cpp
~ClassName() {
    // cleanup code
}
```

---


## Difference Between Constructor and Destructor

| Feature                | Constructor                                      | Destructor                                   |
|-------------------------|--------------------------------------------------|----------------------------------------------|
| **Purpose**             | Used to initialize objects and allocate resources | Used to clean up and release resources       |
| **Invocation**          | Automatically called when an object is created    | Automatically called when an object is destroyed |
| **Parameters**          | Can take arguments (parameterized constructors)   | Cannot take arguments                        |
| **Overloading**         | Can be overloaded (multiple forms allowed)        | Cannot be overloaded                         |
| **Number in Class**     | Multiple constructors can exist in a class        | Only one destructor per class                |
| **Return Type**         | No return type (not even `void`)                  | No return type                               |
| **Naming Rule**         | Same as class name                                | Same as class name prefixed with `~`         |
| **Explicit Call**       | Can be explicitly invoked using object name       | Rarely explicitly called, usually automatic  |
| **Default Availability**| Automatically provided by compiler if not defined | Automatically provided by compiler if not defined |
| **Inheritance Behavior**| Base class constructor runs before derived class constructor | Derived class destructor runs before base class destructor |
| **Resource Management** | Allocates memory, opens files, initializes connections | Deallocates memory, closes files, terminates connections |
| **Polymorphism**        | Not typically virtual                             | Often declared `virtual` in base classes to ensure proper cleanup |
| **Execution Order**     | Runs from base class → derived class              | Runs from derived class → base class         |

---


## Flowchart
### Program 1 - Default Constructors

```
┌───────────────────────────────┐
│            START              │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define class Construct with   │
│ data members a, b             │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define Default Constructor    │
│ → Assign a=10, b=20           │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define displayData() to print │
│ values of a and b             │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ MAIN():                       │
│ Create object obj → invokes   │
│ default constructor           │
│ Call obj.displayData()        │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│            STOP               │
└───────────────────────────────┘
```

---

### Program 2 - Parameterised Constructors

```
┌───────────────────────────────┐
│            START              │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define class construct with   │
│ data members a, b             │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define Parameterized          │
│ Constructor(int m, int n) →   │
│ Assign a=m, b=n               │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define inputdata() to print   │
│ values of a and b             │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ MAIN():                       │
│ Create object aa(10,20)       │
│ Call aa.inputdata()           │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│            STOP               │
└───────────────────────────────┘

```

---

### Program 3 - Copy Constructors

```
┌───────────────────────────────┐
│            START              │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define class student with     │
│ data members rno, name, fee   │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define Parameterized          │
│ Constructor → assigns values  │
│ to rno, name, fee             │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define Copy Constructor →     │
│ initializes from another obj  │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define display() to print data│
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ MAIN():                       │
│ Create s(15,"Student 1",10000)│
│ → Parameterized Constructor   │
│ Call s.display()              │
│ Create student1(s) → Copy     │
│ Constructor called            │
│ Call student1.display()       │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│            STOP               │
└───────────────────────────────┘

```

---

### Program 4 - Destructors

```
┌───────────────────────────────┐
│            START              │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ Define class destruct         │
│ Constructor → increment count │
│ and print "objects created"   │
│ Destructor → decrement count  │
│ and print "objects destroyed" │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│ MAIN():                       │
│ Create objects aa, bb, cc →   │
│ Constructor runs thrice       │
│ Create inner block { dd }     │
│ → Constructor runs once       │
│ → On block exit, Destructor   │
│ of dd is called               │
│ At program end, Destructors of│
│ aa, bb, cc are called         │
└───────────────┬───────────────┘
                │
┌───────────────▼───────────────┐
│            STOP               │
└───────────────────────────────┘

```

---

## Real Life Applications of Constructors and Destructors in C++

### Applications of Constructors
1. **Database Connectivity**
   - Automatically establish a database connection when an object is created.
   - Example: When a `Database` object is instantiated, the constructor opens the connection.

2. **Game Development**
   - Initialize player attributes (health, score, position) when a new player object is created.
   - Example: Setting player health to 100 and score to 0 at the start of a game.

3. **File Handling**
   - Automatically open a file for reading/writing as soon as a `FileHandler` object is created.
   - Ensures that files are always ready for operations without explicit open calls.

4. **GUI Applications**
   - Initialize UI elements (buttons, windows, forms) when an application object is created.
   - Example: A `Window` object’s constructor sets default size, position, and title.

5. **Embedded Systems**
   - Initialize sensors, ports, and hardware modules immediately after object creation.
   - Example: Constructor configures GPIO pins when a `Sensor` object is created.

---

### Applications of Destructors
1. **Database Connectivity**
   - Close the database connection automatically when the object goes out of scope.
   - Prevents resource leaks and maintains data integrity.

2. **Game Development**
   - Save player progress or release memory when the player object is destroyed.
   - Ensures no data is lost when exiting or changing levels.

3. **File Handling**
   - Close files properly when the file object is destroyed.
   - Prevents data corruption and ensures safe file operations.

4. **Dynamic Memory Management**
   - Free dynamically allocated memory to avoid memory leaks.
   - Example: Deallocating arrays or objects created with `new`.

5. **Network Applications**
   - Release network sockets or connections when an object goes out of scope.
   - Ensures proper cleanup of resources and avoids connection leaks.




 


