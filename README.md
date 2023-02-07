# **SISSA Advanced Programming final exam questions**

This file contains a collection of questions (and relative answers) from the final exam of **Advanced Programming** Course, taught by **Prof. Irina Daydenkova** at [SISSA (Trieste, Italy)](https://github.com/sissa) in the academic year 2022-2023.\
The course covers the basics of programming in C++ and Python, and how to interface the two languages.


---

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 1** - Hello world, data types and classes

### Questions

<details><summary>

#### Name at least five variable types in C++.

</summary>

Primitive data types in C++ are `int`, `long int`, `long long int`, `float`, `double`, `char`, `bool`.

</details>

<details><summary>

#### What is *int overflow*?

</summary>

An *int overflow* is a phenomenon that occurs when an integer variable assumes a value that is greater than the maximum value that C++ `int` type can store.

</details>

<details><summary>

#### Why `using namespace std` might not be a good idea?

</summary>

Pulling a specific namespace into the global namespace is not good as it defeats the purpose of namespaces, and can lead to *namespace pollution*.

</details>

<details><summary>

#### Which header do you have to include for the access to `std::cout`?

</summary>

```C++
#include <iostream>
```

</details>

<details><summary>

#### What would be the simplest "legal" program in C++?

</summary>

```C++
int main(){
    }
```

</details>
<details><summary>

#### What is the difference in C++ between `struct` and `class`?

</summary>

The elements of struct are public by default, while those of class are private.

</details>

<details><summary>

#### What does `break` statement do in a loop?

</summary>

It exits the loop without executing the remaining code, even if the condition in the guard is still true.

</details>

<details><summary>

#### What does `continue` statement do in a loop?

</summary>

It skips the execution to the next iteration in the loop, if any.

</details>

<details><summary>

#### How do you define a static array of type `int` and size 7?

</summary>

```C++
int arr[7];
```

</details>

<details><summary>

#### What can you use to read interactive user input?

</summary>

```C++
#include <iostream>
...
std::cin>>x;
...
```

</details>


### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```C++
int a{8},b{8};
if (a=b){
    std::cout<<"equal"<<std::endl
}
```

</summary>

There is a missing semicolon after the `std::endl`.
Moreover, it is better to use the equal operator `==` in the `if` condition.

</details>

<details><summary>

```C++
{int a{2};}
a=4;
```

</summary>

The variable `a` does not exist outside its scope, so it cannot be used unless it is not re-initialized.

</details>

<details><summary>

```C++
double x{0.5},y{0.5};
if(x==y){
    std::cout<<"x is equal to y"<<std::endl;
}
```

</summary>

Comparing `double` variables in this way can lead to error.
In C++, to comprare the equalivalence of two `double` variables it should be compared its difference with a tiny epsilon value.

</details>

<details><summary>

```C++
int x{1},y{1};
while (x<10){
   std::cout<<x<<" "<<std::endl;
   y++;
}
```

</summary>

The `while` loop will never terminate in this way, becuase the condition `x<10` will always be positive unless `x` is increased inside the `while` scope.

</details>

<details><summary>

```C++
int ar[10];
for (int i=0;i<=10;i++){
  ar[i]=i;
}
```

</summary>

The array index are zero-based, so `ar[10]` does not belong to the array.

</details>

<details><summary>

```C++
struct mystruct{
private:
  int a;
  int b;
}
int main(){
  mystruct S;
  S.a=8;
  S.b=7;
  return 0;
}
```

</summary>

Private members of a `struct` can not be accessed from outside the struct definition scope.
Also, a semicolon is missing after the `struct` closing bracket.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 2** - References and pointers, functions, class member functions and constructors

### Questions

<details><summary>

#### What is a reference?

</summary>

A reference is an alias, that is, another name for an already existing variable.
Once a reference is initialized with a variable, either the variable name or the reference name can be used to refer to the same variable.

</details>

<details><summary>

#### What is the difference between passing variables to functions by reference and by value?

</summary>

When passing a variable by value, only the value of the actual parameter is copied to the function's formal parameter: those two types of parameters are stored in different memory locations, so any changes made inside functions are not reflected in the actual parameter of the caller. Instead, when passing by reference, both the actual and formal parameters refer to the same locations, so any changes made inside the function are actually reflected in the actual parameter of the caller.

</details>

<details><summary>

#### Why do we want to pass variables to functions by reference rather than by pointer?

</summary>

To avoid confusion with arrays (which already **are** pointers).
In C++ it is better to use references to pass single variables, while pointers are used for arrays. We can pass by reference when we want that something is not modified nor copied.

</details>

<details><summary>

#### If the function accepts pointers (signature `int function(int* a)`), how do you pass a variable defined as `int x` to it?

</summary>

Putting a `&` in front of the variable name.

</details>

<details><summary>

#### Why do we want to use `const` modifier whenever possible?

</summary>

To ensure that the variable data is not nodified (indeed, it is a constant).

</details>

<details><summary>

#### If you have a pointer named `p`, how do you access a value it points to? What is the name of that process?

</summary>

To access the value, we need to put a `*` before the name of the pointer (`*p`, in this case).
The process is called **dereference**.

</details>

<details><summary>

#### What value is stored in the pointer variable itself?

</summary>

The memory address of whatever the pointer points to.

</details>

<details><summary>

#### What can you say about a function that has signature `void function()`?

</summary>

The function `function()` does not accept any input parameter, could performs some operation and does not return any value. Its return type is `void`. 

</details>

<details><summary>

#### What is an `auto` keyword?

</summary>

`auto` keyword is a placeholder for the actual type of the data, when not know in advice (or multiple options ca be). The `auto` keyword checks on its own what is the return type of the function and applies it.

</details>

<details><summary>

#### What is function overloading?

</summary>

**Function overloading** is the practise of defining multiple functions with the same name, but with different input parameters (in nnumber and types).

</details>

<details><summary>

#### What is a recursive function?

</summary>

To know what is the answer to this question, check the answer of "What is a recursive function?".

Just kidding. It is a function that calls itself.

</details>

<details><summary>

#### What is the role of a constructor in a class?

</summary>

Constructors exist to initialize class member variables.
If no custom parameters are provided, the default constructor initialize the class member with default values.

</details>

<details><summary>

#### How can we change private member variables of a class?

</summary>

Private member of a class can be changed only using a class-member function or a friend function.

</details>

### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```C++
void add_two(int* a){
    a=a+2;
}
int main(){
    int var{0};
    add_two(&var);
    std::cout<<var<<std::endl;
    return 0;
}
```

</summary>

The `add_two` function operates on pointer, so by printing `var` we are actually printing the content of another memory cell.
If the aim of the function is to add 2 to an integer variable, we need to de-reference the pointer by adding a `*` before the name of the pointer in the function corpus.

</details>

<details><summary>

```C++
void swap(int a, int b){
   int temp{a};
   a=b;
   b=a; 
}
int main(){
   int var1{8}, var2{9};
   swap(var1,var2);
   std::cout<<var1<<" "<<var2<<std::endl;
   return 0;
}
```

</summary>

In order to correctly swap the values of the two variables, they should be passed by reference to the function (`swap(int& a, int& b)`).
Also, the `b` variable should take the value of `temp`.

</details>

<details><summary>

```C++
class CMyClass{
    int a;
    CMyClass(int x):a(x){};
}

int main(){
   CMyClass c(7);
   std::cout<<"this won't work"<<std::endl;
   return 0;
}
```

</summary>

If the constructor of `CMyClass` is not made public, it can not be accessed by outside the scope.
Also, a semicolon is missing after the `CMyClass` closing bracket.

</details>

<details><summary>

```C++
int main(){
int x=4;
int& y;

...
}
```

</summary>

a reference has to be initialized when declared. In this case, we should have written `int& y=x;` to have a reference `y` to `x`.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 3** - Makefiles, operator overloads, working with text files


<details><summary>

#### How do you create an object file with `g++`?

</summary>

By running `g++ -c example.cpp`.
This will give us the file `example.o` which is the object file.

</details>

<details><summary>

#### Why can't you just have everything in one file?

</summary>

Because, for big projects, we would end up having files that are too long.

</details>

<details><summary>

#### What is the purpose of a "header guard"?

</summary>

To avoid that a function which is used in multiple files could be redefined from one file to another.

</details>

<details><summary>

#### What does `-IFOLDER_NAME` mean when passed to `g++`?

</summary>

It specifies the folder in which the headers are.

</details>

<details><summary>

#### Do tabs matter in a Makefile?

</summary>

Yes, they cannot be replaced by spaces.

</details>

<details><summary>

#### What does `$@` mean in a Makefile?

</summary>

It evaluates (gives) the name of the current target.

</details>

<details><summary>

#### What does `$^` mean in a Makefile?

</summary>

It evaluates the filenames of all the prerequisites, separated by spaces.

</details>

<details><summary>

#### How to use `make` with a makefile that is not named `Makefile`?

</summary>

`make` has to be followed by the name of the makefile.

</details>

<details><summary>

#### What does it mean if a function is a friend of a class?

</summary>

It can access private member variables of a class.

</details>

<details><summary>

#### Why should non-class member operators be friends of classes?

</summary>

To be able to access their private variables, without having to set the variables of the class as public.

</details>

<details><summary>

#### Which header do you need to include to work with files?

</summary>

```C++
#include <fstream>
```

</details>

<details><summary>

#### How do you open a file in append mode?

</summary>

```C++
filevar.open("file.txt", std::ios_base::app);
```

</details>

<details><summary>

#### What's the main advantage of using templates?

</summary>

Not having to overload a function for every type that we are going to use it with.

</details>

<details><summary>

#### Why do people usually put definitions of templated functions directly into `.hpp` files?

</summary>

(Alessandro Cesa) Because by doing this you don't have to re-define the function in the `main`.

</details>

<details><summary>

#### Except on types, what else can we template on?

</summary>

Integer numbers (meaning anything that is mathematically integer, not just int).

</details>

<details><summary>

#### What is template specialization?

</summary>

Having different codes in the template based on the data type.

</details>

<details><summary>

#### What is a variadic template?

</summary>

* It is a template (a class or function template) which can take a variable number of arguments.
* (Alessandro Cesa) A variadic template is a template with more than one variable, where the type of the templated variable can change.

</details>

<details><summary>

#### Why is using `push_back` for `std::vector` a bad idea?

</summary>

* Because it makes the code slower.
* (Alessandro Cesa) Because you ran out of spaces on the vector, it creates a new one copying the old one, so it makes the code slower.

</details>

<details><summary>

#### How do you pass data from `std::vector` to a "C-style" function that needs a pointer?

</summary>

We can pass vector’s content either as `&myvec[0]` or as `myvec.data`.

</details>

<details><summary>

#### Why you shouldn't use a "vector of vectors"?

</summary>

Because we prefer data to be contiguous in memory.

</details>

<details><summary>

#### How do you allocate a dynamic array in C++?

</summary>

With `new int[N]`.

</details>

<details><summary>

#### What's the difference between `delete` and `delete[]`?

</summary>

They are both used to free memory on a heap.
`delete` is for when we are allocating one object only, `delete[]` is in case we are allocating an array.

</details>

<details><summary>

#### When do you need to create a copy constructor for your class?

</summary>

When we have pointers in our class and need a destructor.
We will also need to overload assignment operator.

</details>

<details><summary>

#### When do you need to create a move constructor for your class?

</summary>

When I want to move an object instead of copying it.

</details>

<details><summary>

#### What should you do if your class allocates resources, but you are sure you will never need a copy constructor?

</summary>

I can use “smart pointers”, from the header memory.
It will automatically call `delete[]` when going out of scope, so I don’t need to manually free memory.

</details>


### **inheritance and dynamic polymorphism** - Lecture 6 (2022-11-08)


<details><summary>

#### What are *protected class members*?

</summary>

*Protected class members* are usually used in inheritance.
They are members that can be accessed only by friends and children (derived) classes.

</details>

<details><summary>

#### What are *virtual functions*?

</summary>

*Virtual functions* are member functions which are declared within a base class and are re-defined (overridden) by a derived class.

</details>

<details><summary>

#### What is an abstract class?

</summary>

An abstract class is a class that is designed to be used as a base class, purely for interface purposes.
It is characterized by the presence of at least one pure virtual function (declared with =0) and it cannot be used as a parameter type, a function return type, or the type of an explicit conversion, and we neither can declare an object of an abstract class.

</details>

<details><summary>

#### Explain dynamic (runtime) polymorphism.

</summary>

Dynamic polymorphism is one of the key features of class inheritance and it indicates that a pointer to a derived class is type-compatible with a pointer to its base class.
It is not recommended in high performance applications since it is slow.

</details>

<details><summary>

#### Why should destructors be made virtual?

</summary>

To avoid memory leaks.
Virtual destructors guarantee that the object of a derived class is destructed properly.

</details>

<details><summary>

#### What is `[](){}()`?

</summary>

`[](){}()` is a lambda expression in C++.
A lambda expression is a way to define an anonymous function (a function without a name) that can be assigned to a variable or passed as an argument to another function.

</details>

<details><summary>

#### What's the general structure of a lambda function?

</summary>

```C++
[capture list](parameter list) -> return_type { function body }
```

</details>

<details><summary>

#### What does `mutable` keyword do in a lambda function?

</summary>

In a lambda function, the `mutable` keyword allows the captured variables to be modified within the body of the lambda, even if they were declared as const in the enclosing scope.

</details>

---

## **<img style="height:3em;vertical-align:middle;margin-right:1em;" src="./images/python.svg"> Python questions**


<details><summary>

#### How do you create markdown cell in Jupyter? (with keyboard commands)

</summary>

Hit the `esc` key.
After that, you can change a cell to Markdown by hitting the `M` key.

</details>

<details><summary>

#### How do you delete a cell in Jupyter (with keyboard command)?

</summary>

Hit the `esc` and then `D` + `D` (press the key twice) to delete the current cell.

</details>

<details><summary>

#### How do you add a cell above the current one in Jupyter (with keyboard command)?

</summary>

Hit the `esc` and then `A`.

</details>

<details><summary>

#### What advantage does *conda* environment provide over a system-wide installation of Python?

</summary>

...

</details>

<details><summary>

#### What does it mean that variables are dynamically typed in Python?

</summary>

...

</details>

<details><summary>

#### What's the difference between Python and C/C++ integers?

</summary>

...

</details>

<details><summary>

#### Explain the difference between lists, sets and tuples in Python.

</summary>

...

</details>

<details><summary>

#### What does negative index mean when accessing list elements?

</summary>

It starts from the last element of the list (e.g `mylist[-1]` means the last element of the list).

</details>

<details><summary>

#### How do you print the first $n$ elements of a list?

</summary>

```python
print(mylist[:n])
```

</details>

<details><summary>

#### How do you print every $n$-th element of a list?

</summary>

```python
print(mylist[::n])
```

</details>

<details><summary>

#### How do you print the reverse list?

</summary>

```python
print(mylist[::-1])
```
or
```python
print(mylist.reverse())
```

</details>

<details><summary>

#### Give an example of a list comprehension.

</summary>

```python
squares = [i*i for i in range(10)]
```

</details>

<details><summary>

#### Give an example of cell and line magic commands in Jupyter.

</summary>

```python
%matplotlib # set up matplotlib to work interactively.
%%pylab     # load numpy and matplotlib to work interactively.
```

</details>

<details><summary>

#### Write a "hello world" function in Python.

</summary>

```python
def helloworld():
    print("Hello world!")
    return
```

</details>

<details><summary>

#### What are keyword function arguments in Python and what is their advantage?

</summary>

...

</details>

<details><summary>

#### Why shouldn't you do `from numpy import *`?

</summary>

...

</details>

<details><summary>

#### What is the advantage of using numpy arrays over lists? What are the dangers?

</summary>

...

</details>

<details><summary>

#### What's the most widely used package for plotting in Python?

</summary>

It is `matplotlib`.

</details>

<details><summary>

#### What's the purpose of `__str__` method in a Python class?

</summary>

...

</details>

<details><summary>

#### What package can you use in Python for symbolic calculations?

</summary>

A library that allows you to do symbolic calculations in Python is `SymPy`.

</details>

<details><summary>

#### What are decorators? Write an example.

</summary>

...

</details>

<details><summary>

#### Name two ways of calling C++ code from Python.

</summary>

...

</details>

<details><summary>

#### What is `pandas`? Name at least 5 functions from that package.

</summary>

...

</details>