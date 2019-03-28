# Variables

The most basic piece of a program is a variable. If you are familiar with variables you can skip to the [Types](#types) section. A variable is a way to name a piece of information so you can refer to it later. It is kinda like a box with a label on it. You want to make the label as descriptive as possible so that you remember what you've put in them. Then you can put things in your box like numbers, characters, strings or other objects. Later in the program you can refer back to them, add them together, print them out, etc... In C++ you have to tell the compiler two things to create a variable: the name by which you will call the variable, and the type of object that it will hold. The next section will talk about that a type is.

# Types

The type system in C++ is said to be *strong*, or in other words, C++ is a *strongly typed* language. This means you tell the compiler what type of thing a variable holds and it can never change. The following is a list of the basic types in C++. This is a very important list and it is important that we get familiar with them:

```cpp
int         \\ integers: ..., -3, -2, -1, 0, 1, 2, 3, ...
float       \\ floating point numbers: -1.0, 2.5, -3.75, 4.125, 3.1415927410125732421875
double      \\ like float but with more decimals: -1.0, 2.5, 3.141592653589793115997963468544185161590576171875

char        \\ a single character: 'a' - 'Z'
std::string \\ an array of characters: "Hello", "World"

bool        \\ a boolean: true or false
```

# Declaring Variables

Whenever we want to declare, or name, a new variable, we have to tell the compiler what type of thing that variable will hold.

```cpp
int i;
```

This declares a variable named `i` and tells the compiler that `i` will hold an integer. Later, you can write

```cpp
i = 3;
```

This assigns the variable `i` the value `3`. Now if I write

```cpp
std::cout << i << std::endl;
```

It will print out the number `3` because that was the value stored in `i`. Because C++ is strongly typed, it would be an error to try and write

```cpp
i = "Hello";
```

Because we told the compiler that `i` holds integers, then we tried to assign `i` a string value. If you try to do this the compiler will not allow it.

Another way to declare variables is to give them a name, a type, and a value all at the same time. This is the preferred way because it can save you from some tricky bugs. Previously when we declared

```cpp
int i;
```

the value of `i` is undefined. It could be zero, or it could be a random value. This is what is called an uninitialized variable. If I tried to print out `i`, I couldn't tell you what it would be. For this reason, it is good practice to give your variables initial values. You can do this the following way.

```cpp
int i = 3;
```

This declares a variable named `i`, tells the compiler that it is an `int` and gives it a value of `3`.

You can declare all types of variables this way.

```cpp
int i = 3;
float f = 1.2;
double d = -4.53;

char c = 'c';
std::string s = "string";

bool b = true;
```

But what good are variables any way? One big thing we can do with variables is some math!

# Arithmetic (math)  Operators

These are our basic mathematical operators to do basic maths. There are other variations that we will discuss in a later topic.

```cpp
+   \\ add
-   \\ subtract
\   \\ divide
*   \\ multiply
%   \\ modulous (the remainder)
```

With these powerful operators we can do some quick maths

```cpp
int i = 1;
int sum = 0;
sum = i+i;
std::cout << sum << std::endl;
// 2
```

This code declares two integers, `i` and `sum` and gives them the values `1` and `0`. Then it adds `i + i` and assigns the result to `sum`. Finally it prints the value of sum which would be `2`.

Doing some simple math is ok but it's kinda boring to hard code all the numbers in. Lets get some user input.

# User Input

To get the user's input we will use something similar to `std::cout`. Instead of going *out* we want to go *in* so we can use `std::cin` instead. This is how that works

```cpp
int i = 0;
std::cin >> i;
std::cout << i;
// prints the number the user typed
```

Notice how the `>>`'s are pointing the other way? This is because we are taking something from the console and putting it into the variable `i`. Then we are taking the value in `i` and printing it back out on the console.

This way we can make our previous example a little more interesting

```cpp
#include <iostream>

int main()
{
  int i = 1;
  int sum = 0;
  std::cin >> i;
  sum = i+i;
  std::cout << sum << std::endl;
  // double the user's input

  return EXIT_SUCCESS;
}
```

One last thing to mention is when you use strings, you need to include the string library too

```cpp
#include <iostream>
#include <string>

int main()
{
  int age = 0;
  std::string name = "";

  std::cout << "enter your name: ";
  std::cin >> name;

  std::cout << "enter your age: ";
  std::cin >> age;

  std::cout << "hello " << name << ", you are " << age << " years old!" << std::endl;

  return EXIT_SUCCESS;
}
```

Try getting this program to compile and run on your computer and see what happens.

# Challenge #2

Navigate to the C++ Github Repository and make sure your branch is checked out. Make a new directory in the submissions directory for challenge #2. Create a new source file called distance.cpp

Write a program to meet the following requirements:

* Ask the user to enter in four numbers. These will represent two (x,y) points on a Cartesian coordinate plane.
* Calculate the distance between the two points 
* Display the result back to the user.

If you need a refresher on the distance formula [google](http://lmgtfy.com/?q=distance+formula) it or checkout the [wikipedia](https://en.wikipedia.org/wiki/Distance#/Mathematics) article.

You'll soon realize that you need to take a square root. You can do this by

```cpp
#include <cmath> // for sqrt

int main()
{
  double number = 4;
  root = std::sqrt(number);

  return EXIT_SUCCESS;
}
```

Have fun with it. Try it in three dimensions instead of two. Make sure you can compile and push it to your branch on github.
