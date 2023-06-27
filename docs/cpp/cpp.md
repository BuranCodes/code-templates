# Code Templates

## **C programming language**

## `Getting a vector of command line arguments`

This one line code snippet allows one to avoid the command of the program being invoked, and get the rest of passed arguments. It then can be parsed further.

### **Code Explanation**

1. A vector of strings is initialized from an array of char pointers `argv`.
2. We start from the second argument (argv[1]), since the first argument (argv[0]) is the command of the program as mentioned above.
3. And we end at the last argument.

### **Usage**

Initalize an vector of command line arguments without the command of the program argument, to be parsed later.

```c++
std::vector<std::string> str(argv + 1, argv + argc);
```
