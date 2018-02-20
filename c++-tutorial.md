* **Compiler**: a program that translate high level language like c++ to machine language

We need a develop tool chain including a compiler 

| Compiler | Platform |
| :--- | :--- |
| MinGW | Windows |
| GCC | Linux |

IDE contains an editor, a compiler, a debugger in a package

| IDE\(Integrated Development Environment\) |  |
| :--- | :--- |
| Eclipse CDT | Linux / Windows |
| Microsoft Visual Studio Express | Windows |
| Code Block | Linux / Windows |
| Xcode | Linux |

For Editor, there are Emacs and Vim.

## Template

```cpp

#include<iostream>
// all the line start with # will be directly read and interpreted by Preprocessor
// it preprocess the code before compiler and include a section header file into program
using namespace std;
// all the elements in C++ standard library is declared within a namespace called std
// This sentence declared which namespace are we using 

int main(){
    cout << "Hello World" << endl;
    return 0;
}
```

Variable is a portion of memory in computer to store a value. Every variable need a name. C++ is a case-sensitive language, so lowercase and uppercase differs from each other.

## Primitive Type 

| Group | Type | size |
| :--- | :--- | :--- |
| Character | char | 8 bit |
|  | char16\_t, char32\_t | 16bit or 32 bit |
| Integer Type \(Signed/Unsigned\) | char | 8 bit |
|  | int | 16 bit |
|  | short | 16 bit |
|  | long | t32 bit |
|  | long long | 64 bit |
| Floating Type | float  |  |
|  | double |  |
|  | long double |  |
| Boolean | bool |  |
| Void Type | void |  |
| Null Type  | null |  |

C++ is a strong typed language which requires every variable was declared with its type before its first use.

String is a compound type.























 

