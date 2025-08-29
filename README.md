/*
================================================================================
README - Constructors and Destructors in C++
================================================================================

🎯 AIM:
    To explore and implement the concept of Constructors and Destructors in C++.

🛠️ SOFTWARE REQUIREMENTS:
    - C++ Compiler (g++/clang++) with C++17 or above
    - Text Editor / IDE (Visual Studio Code, Code::Blocks, or any preferred IDE)

📌 LEARNING OBJECTIVES:
    - Study the role of constructors in object initialization.
    - Differentiate between default, parameterized, copy, and move constructors.
    - Learn about destructors and their importance in memory management.
    - Apply Rule of 3/5/0 in class design.
    - Understand the RAII technique for safe resource handling.

--------------------------------------------------------------------------------
📖 THEORY
--------------------------------------------------------------------------------
1) **Constructor**  
   - A constructor is a special function with the same name as the class.  
   - It is executed automatically when an object is created.  
   - **Types of Constructors**:
        - *Default Constructor* → initializes objects with default values.  
        - *Parameterized Constructor* → initializes objects with custom values.  
        - *Copy Constructor* → creates a new object as a copy of another.  
        - *Move Constructor* → transfers ownership of resources from one object to another.  
        - *Delegating Constructor* → calls one constructor from another within the same class.  

2) **Destructor**  
   - Destructor is a special function prefixed with `~`.  
   - It is automatically called when the object goes out of scope or is deleted.  
   - Mainly used for cleanup such as freeing memory, closing files, or releasing resources.  
   - Must be declared `virtual` in base classes if inheritance is used.  

3) **Rule of 3/5/0**  
   - Rule of 3: If you define *destructor*, *copy constructor*, or *copy assignment*, you should define all three.  
   - Rule of 5: In modern C++, move constructor and move assignment must also be considered.  
   - Rule of 0: Prefer to rely on STL containers and smart pointers so you don’t need custom destructors.  

4) **RAII (Resource Acquisition Is Initialization)**  
   - Ensures resources are tied to object lifetime.  
   - Constructor acquires resources → Destructor releases them.  
   - Makes programs exception-safe and memory-leak free.  

5) **Common Mistakes**  
   - Forgetting to free allocated memory (memory leaks).  
   - Using shallow copy instead of deep copy for dynamic resources.  
   - Missing `virtual` destructors in polymorphic base classes.  

--------------------------------------------------------------------------------
🧪 PROGRAM IMPLEMENTATION
--------------------------------------------------------------------------------
#include <iostream>
using namespace std;

class Demo {
    int value;
public:
    // Default Constructor
    Demo() : value(0) {
        cout << "Default Constructor executed\n";
    }

    // Parameterized Constructor
    Demo(int v) : value(v) {
        cout << "Parameterized Constructor executed\n";
    }

    // Copy Constructor
    Demo(const Demo& d) : value(d.value) {
        cout << "Copy Constructor executed\n";
    }

    // Destructor
    ~Demo() {
        cout << "Destructor executed for value = " << value << endl;
    }

    void display() {
        cout << "Value = " << value << endl;
    }
};

 int main() {
    cout << "\n--- Demonstrating Constructors and Destructor ---\n";
    Demo d1;           // Default constructor
    Demo d2(10);       // Parameterized constructor
    Demo d3 = d2;      // Copy constructor

    d1.display();
    d2.display();
    d3.display();

    cout << "--- End of main() ---\n";
    return 0;
}

--------------------------------------------------------------------------------
✅ CONCLUSION:
    - Constructors provide various ways to initialize objects in C++.  
    - Destructors ensure safe release of resources once the object is no longer needed.  
    - Copy and Move semantics are essential for efficient and correct resource handling.  
    - Rule of 3/5/0 and RAII principles guide modern C++ programming.  
    - Proper design of constructors and destructors prevents memory leaks and ensures program reliability.  
--------------------------------------------------------------------------------
*/
