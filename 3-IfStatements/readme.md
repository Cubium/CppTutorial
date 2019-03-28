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

Okay so now that you have given it a try. Copy this program, compile it, and run it. What happened? What your initial hunch right? Obviously 5 is less that 7. So it will hit the first `if` statement, evaluate it, and return whether or not that is true. Now what do I mean by return `true`? `if` statements are designed by default to enter their scope only if what is in the parentheses is `true`. Okay so change `x` to be equal to `7` (`int x = 7`). What is going to happen? Compile and run the program! This time we got a different print statement! That is because `x` is not less than 7, however, it is equal to 7 because it's value is 7. So the second `if` statement, evaluates to `true` and enters that scope. Alrighty, so now let us change `x` to be equal to `10`. Compile and run your program. You get the gist now right? Let's explain the `if` statement.

```cpp
  if(thingIsTrue)
  {
    doThingInHere;
  }
```

This is pretty much the `if` statement broken down into English. If the `argument/s` inside the parentheses is/are true, then enter the scope and execute the code inside that block. Okay, so let us add the next part:

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

This we have combined with the `else if` statement. Essentially, `else if` is only evaluated if the previous `if` statement's `argument/s` has evaluated to `false`. Let us add the last one now:


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

The final `if` statement is the `else` statement. This basically means, everything above me has evaluated to `false` so therefore I am `true` and I will execute this piece of code. These are very powerful to use and we will be playing with them shortly!

Note, that you can chain `if` statements together, but be careful! They can have **unintended** consequences if you are not thinking about it logically! For example:

```cpp

  if(thingIsTrue)
  {
    doThingInHere;
  }
  if(thingIsTrue)
  {
    doThingInHere;
  }
```

So if you have two `if` statements and the thing that is true evaluates to `true` in both arguments, both will execute their codes! So try and pay attention to when you need `else if` vs another `if`. If you have a ton of arguments that you need to evaluate, you can also do:

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
  else if(theAboveIsNotTrueButThisIsTrue)
  {
    doThingInHere;
  }
  else
  {
    everthingElseHasFailedSoThisIsTrue;
  }
```

I think you get the picture! So let us move onto logical arguments. Ever heard of a truth table? Well let's have a look at the `&&` (and) operator's truth table:

```
a  b  a && b
============
T  T       T
T  F       F
F  T       F
F  F       F

```

How do we read it? Basically first line underneath the equal signs says: "If a is true, and b is true, then a AND b is true". You can piece together the rest, know this by heart! Now let us look at the `||` (or) operator's truth table, this time say to yourself "If a is true, or b is true, then a or b is true":

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

Compile and run this program. What happened? You saw multiple lines print on your screen and you are probably wondering why that is. Well try and break it down. Why did multiple lines print out? Well that is because of two things: The first, is because I used nothing but `if` statements. Remember what I said could happen? If you don't write your logic out carefully, then you can have some really wonky stuff go on with your code that you don't want to have happen. Try playing with this code! Is there something you can do to make sure that only one line prints?

# Challenge 3

Now that you have an idea of what to do with if statements let's write a program using the previous knowledge that you have gained! 

Write a simply grading program with the following criteria:

user input from the command line into an integer called `score`. (`std::cin`)

The program will report an output of a grade A if the score is above 95. (Sundberg Standards xD)
A grade B if the score is between 80 and 95.
A grade C if the score is between 70 and 80.
A grade D if the score is between 60 and 70.
And a grade F for anything below 60. 

Have fun with it! And remember to submit your code on your branch! Reach out if you need any help!
