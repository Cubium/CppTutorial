# Fun with Functions

Woot! So we are now here to one of my favorite topics: Functions! 

So what is a function? Well I like to think of functions like we think of functions in mathematics, so let us start there.

`f(x) = x + 4` This is a mathematical function that we should be very familiar with by this point in our lives. What happens when `x = 2`? Well, plug it into our function and let's find out! `f(2) = 2 + 4`, thus, `f(2) = 6`. Well that was easy wasn't it? Well let's step it up a notch, what if we have the function: `f(x,y) = x + y`? Well same thing! Let us set `x = 5` and `y = 3` and let us plug it into our function: `f(5,3) = 5 + 3`, thus, `f(5,3) = 8`. See how easy that is? 

To put it in English terms, when we call a function we should expect something in return. In this case, we gave our function a number and we received a number in return. In C++ functions work the exact same way. So let us go ahead and dive into actual implementations of functions. But first, I will give you a program for you to try and read. Remember, try and read the program before compiling it yourself. What is the program doing?

```cpp

#include <iostream>

void printHello()
{
  std::cout << "Hello, ";
}

void printWorld()
{
  std::cout << "World!" << std::endl;
}

int main()
{
  printHello();
  printWorld();

  return EXIT_SUCCESS;
}

```

Go ahead and compile and run this code now. Was your intuition correct? Why did it work? What happens if you decide to put `printWorld()` before `printHello()`? Go ahead and try it! Let us talk about basic rules to follow when it comes to functions:

# Rules

### Rule #1 Top Down

Remember that C++ is a top down language. As a reminder, that your compiler reads everything from the top all the way down to the bottom. The following code is not legal or will not compile:

```cpp
#include <iostream>

void printHi()
{
  std::cout << "Hi ";
  printThere();
}

void printThere()
{
  std::cout << "there!" << std::endl;
}

int main()
{
  printHi();
  
  return EXIT_SUCCESS;
}
```
`printThere()` has not been declared yet, and the compiler will look at the function `printThere()` above the function `printHi()`. And when the compiler does not find the function `printThere()` it will stop dead in it's tracks and tell you to please fix this. So remember, when you are declaring a function in the same file, you have to do it in a top-down way.

What if you want to be able to do this? Well there is a handy-dandy tool called `function prototyping` meaning, we define the function before we implement it. What do I mean by that?

```cpp
#include <iostream>

void printHi();
void printThere();

int main()
{
  printHi(); 
}

void printHi()
{
  std::cout << "Hi ";
  printThere();
}

void printHi()
{
  std::cout << "there!" << std::endl;
}
```
What I have done here is told the compiler. "Hey, I have a function named `printHi()` and `printThere()`. That I will define later. I just wanted to give you a heads up." The compiler is okay with this, and will compile this code, only because the compiler now knows that `printHi()` and `printThere()` exists. 

### Rule #2 Try to keep each function to seven lines

As Dr. Kenneth Sundberg has told many of his students. If you have too many lines of code in a function, then you can probably break them up into a function to make it more readable. When there are too many lines of code within one block, it becomes difficult to read and thus becomes difficult to follow. Take a look at the following code:

```cpp
#include <iostream>

int main()
{
  int x;
  int y;
  int sum;
  
  int x2;
  int y2;
  int sum2;

  int sum3;
  
  x = 4;
  y = 5;
  sum = x + y;
 
  std::cout << sum << std::endl; 
  
  x2 = 7;
  y2 = y;
  sum2 = x2 + y2;  
  
  std::cout << sum2 << std::endl; 

  sum3 = sum + sum2;

  std:cout << sum3 << std::endl;

  return EXIT_SUCCESS; 
}
```

I don't know about you, but this physically hurts to read this and there is a lot going on here. Especially when we can break this all up into functions to help us out. A lot of programming is about code reuse. Try not to repeat yourself when you do not need to! Try and look through your code, where can you use functions to help yourself out here?

```cpp
#include <iostream>

int getSum(int x, int y)
{
  return x + y;
}

void printSum(int sum)
{
  std::cout << sum << std::endl;
}

int main()
{
  int x = 4;
  int y = 5;
  
  int sum = getSum(x,y);
  printSum(sum);

  x = 7;
  int sum2 = getSum(x,y);

  printSum(sum2);
  
  int sum3 = sum + sum2;
  printSum(sum3);
  
  return EXIT_SUCCESS; 
}
```

Okay, you're probably giving me a lot of crap right now. "But Raul! You have 9 lines of code in main! Not 7!" My response to you is, this is true, but I have now reduced 17 lines of code down to 9 lines in a single block. Also, look how much more readable that code is. It is really straight forward on what is happening with this code. 

### Rule #3 Use Meaningful function names

Arguably the most difficult thing in software engineering and software development is naming things. Naming objects is really hard, but we do need to do our best to go ahead and name functions that mean something. Don't do the following:

```cpp
#include <iostream>

int doSomethingCool(int something)
{
  something = 15;
  return something;
}

int doAnotherCoolThing()
{
  return 4;
}

int main()
{
  int whoCares = doAnotherCoolThing();
  whoCares = doSomethingCool(whoCares);

  std::cout << whoCares << std::endl;

  return EXIT_SUCCESS;
}

```

Do you know what any of that does at first glance while reading it? I know what it does because I wrote it. However if I have someone else look over this code, then they have to look through this and try and decipher this archaic mess and make sense of it for themselves. Instead, do this:

```cpp
#include <iostream>

int reassignX(int x)
{
  x = 15;
  return x;
}

int setXTo4()
{
  return 4;
}

int main()
{
  int x = setXTo4;
  x = reassignX(x);

  std::cout << x << std::endl;

  return EXIT_SUCCESS;
}
```
This is much more readable and we know exactly what each function is supposed to do. So to re-iterate. Name your functions something meaningful.

### Rule #4 Only perform what your function says it will do

Remember that functions need to stay as pure as possible. This is a highly argued topic within programming and is up to the reader on how they implement functions. However one should definitely not over saturate or complicate functions when they have the power to do so. Remember, functions should only return one object, they should try to avoid modifying objects that do not belong to that function. For example:

```cpp
#include <iostream>
#include <string>

int getSum(std::string &name, int x, int y)
{
  name = "John";

  return x + y;
}

int main()
{
  std::string name = "Bob";
  int x = 7;
  int y = 5;

  std::cout << name << std::endl;

  int sum = getSum(name, x, y);

  std::cout << name << " " << sum << std::endl;

  return EXIT_SUCCESS;
}
```

This breaks Rule \#3 as well, since we are also not just getting the sum of the function. We are also modifying the name of the string `name`. And this is not good programming practice. If you must modify the name of a string, then create a separate function called `changeName`.

### Rule #5 Return what you promise

Exactly what that reads. Return what you promise that you state what your function will do. If you have a function that is called `getSum` then return the sum. If you have a function called `updateLocation` then update the location. This will make your programming much more readable and less confusing. Do not do the following:

```cpp
#include <iostream>

int getSum(int x, int y)
{
  return 5;
}

int main()
{
  int x = 5;
  int y = 10;

  int sum = getSum(x,y);

  std::cout << sum << std::endl;
}
```
This code happily compiles, because you promised the integer `sum` that it will get back an integer. However this isn't returning a summation of x and y, it is returning the number 5. A good compiler with all the warning flags turned on will tell you that `y` is not used. So to re-iterate. Return what your function promises to return.

# Types of Functions

A function can be created with any type. However, you must return the exact value of that function that you have defined for it. The exception in this case is `void()`. A `void()` function is a function with no return type. These are commonly used when you do not need to return anything. Examples are printing. Here is a short example of how to use functions:

```cpp
#include <iostream>
#include <string>

void printHi()
{
  std::cout << "Hi." << std::endl;
}

int genInt()
{
  return 5;
}

double genDouble()
{
  return 2.3;
}

float genFloat()
{
  return 4.5;
}

char genChar()
{
  return 'a';
}

std::string genString()
{
  return "A String";
}

int main()
{
  printHi();

  int x = genInt();
  double y = genDouble();
  float z = genFloat();

  char letter = genChar();
  std::string aString = genString();
}

```

# Passing variables into functions

Okay, now that you have read the rules and are now familiar with the types we will now go ahead and talk about passing variables into functions. You probably saw `&` and you were probably confused on what that meant. Don't worry! I will do my best to make this less scary for you! This was a REALLY hard topic for me to grasp for a long time so I will do the best I can to explain this clearly. If you ever have any questions do not hesitate to contact us. 

### Pass by Value (Copy)

Let us look at the following function:

```cpp
void swap(int x, int y)
{
  int temp = x;
  x = y;
  y = temp;
}
```
Here we have passed `x` and `y` by value. In other words, we have asked the compiler to make a copy of both of these variables when they enter this scope. What do I mean by that? Well, let me write this example down in a small story:

Say that you are a machinist and you need a piece of metal that you just machined painted. However, you would still like to keep your piece of unpainted metal and you decide to make a copy of that piece of metal to send to the painter. So you send your copy to the painter and you still keep the original. The painter then paints the copy and then returns that to you. You then decide you like that painted copy so you throw away the original and you replace it with the newly painted copy.

That is what pass by value means, we hand the compiler a copy of the variable that we handed it and ask it to do something with that copy. In this case, we have handed copies of `x` and `y` to the function `swap` and asked them to swap. However, we passed it into a `void()` function, meaning we will not get these copies back. Take a look at the following program:

```cpp
#include <iostream>

void print(int x, int y)
{
  std::cout << x << " " << y << std::endl;
}

void swap(int x, int y)
{
  int temp = x;
  x = y;
  y = temp;
}

int main()
{
  int x = 7;
  int y = 5;
  
  print(x,y);

  swap(x,y);

  print(x,y);
  


  return EXIT_SUCCESS;
}
```

Here we assigned the integers `x` and `y` to 7 and 5. We then wrote a function for them to swap values. However, since we passed these by value, we will not see the outcome because the function `swap` received copies of the integers and not their addresses. I will explain what I mean by address in the next header. 

When is passing by value good? Here in the industry I have heard people say, "You should never pass anything by value! Everything should be passed by reference!" This is debatable. In this case, the size of the integers `x` and `y` are so small that it will not affect performance in any way. This is a personal preference, but I feel it is safe to assume that when you are dealing with any numbers that it is okay to pass them by value. It is also good if you need to keep your original copy of the thing that you are passing in.

When is passing by value bad? I just showed above an example of why passing by value is bad. If you need to make a modification to that value and you do not need to keep a copy, then you should pass it by reference. The biggest no-no of passing by value is if you have a HUGE object that already eats up a lot of memory. Say you have a container that has one million elements stored inside of it. That is a huge container, and if you pass that container by value, then you have created another container of one million elements and now you have TWO containers of one million elements. So this is a big no-no. It is safe to say that any container, object, or string, should not be passed by value.

### Pass by Reference

Let us look at the same function except now it has a small change that makes a HUGE difference. In order to pass by reference we will now be introduced to the `&` operator. This is not to be confused with the operator `&&`, that is `and` the operator I have introduced to you is the reference operator:

```cpp
void swap(int &x, int &y)
```
This is called pass by reference. Meaning that we have passed the address of `x` and `y` into the function. What do I mean by address? When you declared the integer `x` and `y`, your compiler assigned their physical locations to somewhere in your computer's memory. So `x` and `y` officially have homes! You can even print out the address if you do `std::cout << &x << std::endl;` You'll get some hexidecimal number back, but that is where the address of `x` is. 

Okay so back to the story that I wrote. Say this time the machinist creates a piece of metal that needs to be painted. However, this time the machinist sends the original piece of metal to the painter. The painter then paints the piece of metal and returns it back to the machinist. So instead of having two copies of the piece of metal, the machinist has only one copy and it has been painted.  

This is passing by reference. When we pass by reference we pass the address to the variable or object that we created. We aren't passing a physical copy of the variable or object. We are passing the address to the object. Take a look at our modified program now:

```cpp
#include <iostream>

void print(int x, int y)
{
  std::cout << x << " " << y << std::endl;
}

void swap(int &x, int &y)
{
  int temp = x;
  x = y;
  y = temp;
}

int main()
{
  int x = 7;
  int y = 5;
  
  print(x,y);

  swap(x,y);

  print(x,y);

  return EXIT_SUCCESS;
}
```
Now swapping the two numbers works. We have passed them by reference so `swap` is now modifying the original `x` and `y`. It has not received a copy of `x` and `y` but it has received their addresses. So try and get that cemented in your head. Sometimes this is easy for people to grasp, others like myself, took a long time to truly understand what that means. 

When is it good to pass by reference? It is good to pass by reference when you need to make a modification to the value without creating a copy. This is especially important to know when you have that container of one million elements. Instead of created two containers of one million elements, you only use the original container that you gave it. Passing by reference can be very memory efficient. And when you are working in a language that boasts speed and efficiency. You have to know about when to pass by reference and when not to. 

When is it bad to pass by reference? When you DO NOT want to make ANY, and I mean ANY, modifications to the variable or container you pass it. I cannot stress this enough. C++ is a adult language. It does not hold your hand and it will do whatever you ask it to do. This can be extremely dangerous if you are creating a critical piece of software and you accidentally modify an address to your variable or container. If you know that you do not need to modify a variable or a container. Then you should pass it by constant reference or by value. 

### Pass by Constant Reference

So now I will introduce you to a keyword that we may have mentioned before: `const`, this means constant. Meaning that when we declare a variable constant, we cannot modify, or re-assign it's value. (Really, this is C++ and you can do whatever you want and in reality you can modify a `const` variable with some work but don't do it!) So what do I mean by `const` reference? Let's modify our code and I'll show you what I mean:

```cpp

#include <iostream>

void print(int x, int y)
{
  std::cout << x << " " << y << std::endl;
}

void swap(const int &x, const int &y)
{
  int temp = x;
  x = y;
  y = temp;
}

int main()
{
  int x = 7;
  int y = 5;
  
  print(x,y);

  swap(x,y);

  print(x,y);

  return EXIT_SUCCESS;
}
```
Try compiling this code. It throws an error right? Why? Because we told the function swap, "I have given you two constant variables. Do not modify them!" So our compiler get's mad at us and asks us to fix it. So what does the reference do? Well it's the same thing as passing a value by reference. We have passed the address to the integers however we have asked the compiler to not modify them in any way. 

When is it good to pass by `const` reference? When you DO NOT want to make ANY modifications to your variables or containers! These are very good for reading for example, most strings and most containers if you are only performing then you want to pass by `const` reference. For example:

```cpp
void printString(const std::string &toPrint)
{
  std::cout << toPrint << std::endl;
}
```
This passes the string `toPrint` by constant reference. So the only thing we can do with this is read from it. And that is what `std::cout` does, it only reads the value. So when is it good to pass by `const` reference? When you need a variable to be read only.

When is it bad to pass by `const` reference? When you need to make a modification to your variable. In this case, swap cannot perform what it needs to do because the values are constant. 

# Challenge #5 Part 1

# Challenge #5 Part 2
