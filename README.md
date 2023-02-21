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

### Questions

<details><summary>

#### How do you create an object file with `g++`?

</summary>

By running `g++ -c example.cpp`.
This will give us the file `example.o` which is the object file.

</details>

<details><summary>

#### Why can't you just have everything in one file?

</summary>

Because, for big projects, we would end up having files that are too long. This makes difficult to navigate through the code.
Dividing the preject in multiple files is also useful for re-using part sof code.

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

`make` has to be followed by the flag `-f` and the name of the makefile.

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
ofstream filevar;
filevar.open("file.txt", std::ios_base::app);
```

</details>

### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```C++
CCoords CCoords::operator+(const int& b) {
        CCoords result;
        result.x = x + b;
        result.y = y + b;
        return result;
    }
int main(){
    CCoords c;
    c.x=0;c.y=3;
    auto cc=2+c;
}
```

</summary>

As it is defined, the *plus* operator is not commutative, so you can not sum an integer and a CCords in this order.

</details>

<details><summary>

```C++
class MyClass{
  int x;
  MyClass():x(0){};
}
std::ostream& operator<<(std::ostream& os, const MyClass& m){
    os<<m.x<<std::endl;
    return os;
};
int main(){
    MyClass m;
    std::cout<<m<<std::endl;
}
```

</summary>

Constructor should be made *public*, and the signature of the friend function should be inside the class.

</details>

<details><summary>

```C++
int result;
for(int i=0;i<N;i++){
   result=calculate_result();//valid function defined somewhere else
   std::ofstream filevar("results.txt");
   filevar<<result<<std::endl;
   filvar.close();
}
```

</summary>

If not opening the file in *append mode*, the content of it is being overwritten every time in the `filevar<<result<<std::endl` line, so it does not make sense do a loop since no effects will take place. Also, `filvar` is mis-spelled in the last code line.

</details>


## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 4** - Templates, arrays and vectors

### Questions

<details><summary>

#### What's the main advantage of using templates?

</summary>

Not having to overload a function for every type that we are going to use it with.

</details>

<details><summary>

#### Why do people usually put definitions of templated functions directly into `.hpp` files?

</summary>

Because otherwise you should re-define the function in the `main` file.

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

A variadic template is a template with more than one variable, where the type of the templated variable can change.

</details>

<details><summary>

#### Why is using `push_back` for `std::vector` a bad idea?

</summary>

Because if you ran out of spaces on the vector, it creates a new one copying the old one, so it makes the code slower.

</details>

<details><summary>

#### How do you pass data from `std::vector` to a "C-style" function that needs a pointer?

</summary>

We can pass vector’s content either as `&vec[0]` or as `vec.data`.

</details>

<details><summary>

#### Why you shouldn't use a "vector of vectors"?

</summary>

Because we prefer data to be contiguous in memory.

</details>


### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```C++
template <typename T>
class CMyClass{
  T a;
  T b;
}

int main(){
  CMyClass var;
 ...
}
```

</summary>

It should be specified the `var` data type (with triangular brackets).

</details>

<details><summary>

```C++
template <typename T, double S>
void add_number(T& var){
    T=T+S;
}
```

</summary>

In the function body, `var` should be used instead of `T`. Also, non-type parameter can only be integers (not `double`).

</details>

<details><summary>

```C++
template <typename... Types>
void myPrint(const Types&... args){
    std::cout<<arg<<" ";
    myPrint(args...);
}
```

</summary>

You should template on type `T`, and the define a function for printing a single element.

</details>

<details><summary>

```C++
template <typename T>
void print(const T& var){
  std::cout<<var<<std::end;
}

struct MyClass{
  int a;
  int b;
}

int main(){
 MyClass var;
 print(var);
}
```

</summary>

Operator `<<` should be overloaded in the struct. 

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 5** - Memory menagement

<details><summary>

#### How do you allocate a dynamic array in C++?

</summary>

With `int *arr = new int[N]`, or using smart pointers.

</details>

<details><summary>

#### What's the difference between `delete` and `delete[]`?

</summary>

They are both used to free memory on a heap.
`delete` is for when we are allocating one object only, `delete[]` is in case we are deleting an array.

</details>

<details><summary>

#### When do you need to overload assignment operator for your class?

</summary>

When there are pointers inside the class, otherwise an assignment would just create a "shallow copy" (it copies the pointer to the data, not the data itself), and when the original object is deleted, the copy will point to a non-existing memory location, thus making the destructor not able to delete it. As a general rule, if you have pointers in your class and need a destructor, it's better to overload the assignment operator and the copy constructor.

</details>

<details><summary>

#### When do you need to create a copy constructor for your class?

</summary>

When it is needed to pass by value an instance of the object.

</details>

<details><summary>

#### When do you need to create a move constructor for your class?

</summary>

When I want to move an object instead of copying it.

</details>

<details><summary>

#### What should you do if your class allocates resources, but you are sure you will never need a copy constructor?

</summary>

You could overload the function with a `delete`.
It will automatically call `delete[]` when going out of scope, so I don’t need to manually free memory.

</details>


## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 6** - Inheritance and dynamic polymorphism

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

### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```C++
class Shape{
 public:
  virtual void print()=0;
  virtual ~Shape(){};
}

class Circle: public Shape{
  double r;
  void print() override {std::cout<<r<<std::endl};
  }

int main(){
  Shape s;
  Circle c; 
}
```

</summary>

Since `Shape` is an abstract class, it is not possible to define `Shape s;` in the `main()` function.

</details>

<details><summary>

```C++
class Shape{
 public:
  virtual void print(){};
  ~Shape(){};
}

class Polygon: public Shape{
  double* v;
  void print() override {std::cout<<"hi"<<std::endl};
  Polygon(const int&N){v=new double[N];};
  ~Polygon(){delete[] v;};
  }

int main(){
  Shape* s = new Polygon(7);
  s.print();
}
```

</summary>

The constructor, destructor and `print()` functions in `Polygon` have to be made public. Being `s` a pointer, `s.print()` has to be written as `s->print()`.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/C++.svg"> **Lesson 7** - Command line parameters

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

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 8** - Python basis, Jupyter

<details><summary>

#### How do you create markdown cell in Jupyter? (with keyboard commands)

</summary>

Hit the `esc` key.
If you want to add a cell above the current one, press `A`. If you want it below, press `B`.
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

It separates development environments, ensuring that project have compatible versions of the needed libraries.

</details>

<details><summary>

#### What does it mean that variables are dynamically typed in Python?

</summary>

It means that Python let the variable change in data types (for example, an `int` variable can assume `string` data type, or viceversa).

</details>

<details><summary>

#### What's the difference between Python and C/C++ integers?

</summary>

Python integers are represented as a class, and are less likely to occur in overflows.

</details>

<details><summary>

#### Explain the difference between lists, sets and tuples in Python.

</summary>

A list is a mutable, resizable, ordered group of variables. A set is a mutable group of distinct variables. A tuple in Python is an ordered, non-mutable group of variables.

</details>

<details><summary>

#### What does negative index mean when accessing list elements?

</summary>

It access the list from the last element (e.g., `mylist[-1]` access the last element of `mylist` list).

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
%% file.txt # saves the current cell content into a file
% timeit # calculate computation time of the selected command
```

</details>

<details><summary>

#### Write a "hello world" function in Python.

</summary>

```python
def hello_world():
    print("Hello world!")
    return None
```

</details>

<details><summary>

#### What are keyword function arguments in Python and what is their advantage?

</summary>

They are arguments that can be passed to a function by name, so the order does not matter. For esample, a function defined to work with parameters `a` and `b` can be called either by `fun(a=1, b=2)` or `fun(b=2, a=1)` and produces the same result.

</details>

### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```python
if x==0:
print('x is zero')
elif x>0:
print('x is greater then zero')
elif x<0:
print('x is smaller than zero')
```

</summary>

No indentation is an error in Python.

</details>

<details><summary>

```python
t = tuple(range(10))
t[5]=100
print(t[5])
```

</summary>

Tuples are immutable, so it is not possible to modify a tuple element.

</details>


## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 9** - Numpy, Matplotlib

<details><summary>

#### Why shouldn't you do `from numpy import *`?

</summary>

To avoid namespace pollution. If you do so, you are not sure about the origin of used functions in the file (that can be overwritten by different libraries).

</details>

<details><summary>

#### What is the advantage of using numpy arrays over lists? What are the dangers?

</summary>

Numpy arrays are optiized for computation speed. It is needed to take particular caution when using numpy arrays, because rows are sometimes created by reference rather than by allocating new memory, so modifing a row affects all the others. Numpy arrays int overflows are possible.

</details>

<details><summary>

#### What's the most widely used package for plotting in Python?

</summary>

It is `matplotlib`. The `pyplot` module can be imported with `from matplotlib import pyplot as plt`.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 10** - Python classes

<details><summary>

#### What's the purpose of `__str__` method in a Python class?

</summary>

To print the object when system function `print(obj)` is called.

</details>

### Code snippets

Find the errors in the following *code snippets*:

<details><summary>

```python
class MySecondClass:
    def __init__(number):
        self.number = number
a=MySecondClass(4)
```

</summary>

The `__init__` function takes also `self` as (first) argument.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 10** - SymPy, Decorators

<details><summary>

#### What package can you use in Python for symbolic calculations?

</summary>

A library that allows you to do symbolic calculations in Python is `SymPy`.

</details>

<details><summary>

#### What are decorators? Write an example.

</summary>

Decoratrors are function in Python that operates "on top" of other functions, modifing the output without modifing the function itself. An example:

```python
def my_decorator(fun):
  def wrapped(*args, **kwargs):
    return -fun(*args, **wkargs)
  return wrapper
```

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 10** - Cytypes

<details><summary>

#### Name two ways of calling C++ code from Python.

</summary>

One possible way of calling C++ code from Python is using the `Cython` package, or `pybind` package.

</details>

## <img style="height:1em;vertical-align:middle;margin-right:.2em;" src="./images/python.svg"> **Lesson 11** - Pandas

<details><summary>

#### What is `pandas`? Name at least 5 functions from that package.

</summary>

It is a Python library for working with Datasets. Functions examples are `pd.read_csv()`, `pd.DataFrame.to_csv()`, `pd.DataFrame.reset_index()`, `pd.DataFrame.drop()`, `pd.DataFrame.dropna()`.

</details>