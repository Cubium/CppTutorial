# If Statements

So here we are! We are moving up in the world and each lesson we learn something new! So lets start with Logic! 

Well what about logic? Well it is important that we know how to use `if`, `else if`, and `else` statements. We can even go as far as using `switch` statements. However for now we are going to focus on the first three heavily. So let's get started with looking at this simple program down below:

```cpp
#include <iostream>

int main()
{
  
  int x = 5;
  int y = 7;

  if(x < y)
  {
    std::cout << x << " is less than " << y << std::endl;
  }
  else if(x == y)
  {
    std::cout << x << " is equal to " << y << std::endl;
  }
  else
  {
    std::cout << x << " is greater than " << y << std::endl;
  }

  return EXIT_SUCCESS;
}
```

Before you copy this program to compile and run yourself try and read this code. What do you think will happen? What is going on? Try and get comfortable with the syntax and break it down. The more time you spend reading it now, it will become a lot less intimidating in the future!

Okay, now that you have given it a try, copy this program, compile it, and run it. What happened? Was your initial hunch right? Obviously 5 is less that 7, so the condition in the first `if` statement will be true and the statement inside will be run and the rest will be skipped. `if` statements only execute the statements inside them if the condition in parentheses is `true`. Then all other `else if` and `else` are skipped. 

Okay so change `x` to be equal to `7` (`int x = 7`). What is going to happen? Compile and run the program! This time we got a different print statement! That is because `x` is not less than 7, however, it is equal to 7 because it's value is 7. So the condition in the second `if` statement evaluates to `true` and the program enters that scope. Alrighty, now let's change `x` to be equal to `10`. Compile and run your program. This time, since `x < y` is false, and `x == y` is false, the program goes into the `else` statement. The else is a "catchall"; no matter what is in the previous conditions, if they are all false, the else statement will be executed.

```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
```

This is pretty much the `if` statement broken down into English. If the `condition/s` inside the parentheses is/are true, then enter the scope and execute the code inside that block. Okay, so let us add the next part:

```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
  else if(theAboveIsNotTrueButThisIsTrue)
  {
    doThingInHere;
  }
```

Here we have combined the `if` with the `else if` statement. Essentially, `else if` is only evaluated if the previous `if` statement's `condition/s` has evaluated to `false`. Let us add the last one now:


```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
  else if(theAboveIsNotTrueButThisIsTrue)
  {
    doThingInHere;
  }
  else
  {
    everthingElseHasFailedSoThisIsTrue;
  }
```

The final `if` statement is the `else` statement. This basically means, everything above me has evaluated to `false` so therefore I am `true` and I will execute this piece of code. These are very powerful to use and we will be playing with them shortly! Note, you can have as many `else if` statements as you want:

```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
  else if(theAboveIsNotTrueButThisIsTrue)
  {
    doThingInHere;
  }
  else if(theAboveIsNotTrueButThisIsTrue)
  {
    doThingInHere;
  }

  ... more else if's

  else
  {
    everthingElseHasFailedSoThisIsTrue;
  }
```
Note, just like the `else` is optional, so are the `else if`. You can have as many as you want or zero. It all depends on what you need to get done.

```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
  else
  {
    guessTheFirstThingWasn'tTrue
  }
```

Note, that you can chain plain `if` statements together, but be careful! They can have **unintended** consequences if you are not thinking about it logically! For example:

```cpp

  if(thing1IsTrue)
  {
    doThingInHere;
  }
  if(thing2IsTrue)
  {
    doThingInHere;
  }
```

So if you have two `if` statements and `thing1` and `thing2` are `true`, then both will execute their statements!

I think you get the picture! So let us move onto logical arguments. Ever heard of a truth table? Well let's have a look at the `&&` (and) operator's truth table:

```
a  b  a && b
============
T  T       T
T  F       F
F  T       F
F  F       F

```

How do we read it? The first line under the equal signs says: "a is true, b is true, then a AND b is true". And requires both sides to be true in order for the whole statement to be true. That's why the second line says "a is true, b is false, then a AND b is false". You can piece together the rest, know this by heart!

Now let us look at the `||` (or) operator's truth table, this time say to yourself "a is true, b is true, then a or b is true". As long as one or the other or both sides is true, the whole statement is true:

```
a  b  a || b
============
T  T       T
T  F       T
F  T       T
F  F       F

```

Great! Now with our new found knowledge of truth tables let us put them to use! Again, like the above code, try and read this code before copying and compiling it yourself. What do you think it is doing?

```cpp

#include <iostream>
#include <string>

int main()
{
  std::string firstName1 = "John";
  std::string lastName1 = "Smith";
  std::string firstName2 = "Mary";
  std::string lastName2 = "Smith";

  int johnAge = 22;
  int maryAge = 20;

  if(firstName1 == firstName2 && johnAge < 25)
  {
    std::cout << "Well this is odd...they share the first name AND John's age is less than 25!" << std::endl;
  }
  if(firstName1 == firstName2 || johnAge < 25)
  {
    std::cout << "Well this is odd...either they share the same first name OR John's age is less than 25!" << std::endl;
  }
  if(lastName1 == lastName2 && johnAge > maryAge)
  {
    std::cout << "They both share the same last name AND John is older than Mary" << std::endl;
  }
  if(lastName1 != lastName2 || johnAge > maryAge)
  {
    std::cout << "They eiher both don't have the same last name OR John is older than Mary" << std::endl;
  }

  return EXIT_SUCCESS;
}

```

Compile and run this program. What happened? You should see multiple lines print on your screen. Let's break it down. Why did multiple lines print out? Well that is because of two things: The first, is because I used nothing but `if` statements. Remember how if statements work? If statements only skip to the end if they are a chain of `if`, `else if`, and `else`. Try playing with this code! Is there something you can do to make sure that only one line prints?

# Challenge 3

Now that you have an idea of what to do with if statements let's write a program using the previous knowledge that you have gained! 

Write a simple grading program with the following criteria:

The user will input from the command line into a variable called `score`. (use `std::cin`)

The program will report the grade to be an `A` if the score is equal to or above 95. (Sundberg Standards xD)
A `B` if the score is between 80 and 95.
A `C` if the score is between 70 and 80.
A `D` if the score is between 60 and 70.
And an `F` for anything below 60. 

Ex:
Enter your score: 94
B
Enter your score: 95
A

Have fun with it! And remember to submit your code on your branch! Reach out if you need any help!
