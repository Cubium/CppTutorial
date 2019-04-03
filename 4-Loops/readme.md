# Loops

This lesson is a continuation of the discussion on control flow. The next step after if statements is loops. Loops are powerful structures that allow you to repeat a block of statements many times. There are two kinds of loops, _for_ loops and _while_ loops. We'll start with the simpler of the two, the while loop.

# While Loops

A while loop looks like this

```cpp
while ( condition )
{
  // code to run
}
```

So **while** the condition evaluates to true, the loop will run one more time. Then the condition is rechecked and the loop will keep running until the condition is false. Here is a practical example of a while loop

```cpp
#include <iostream>

int main()
{
  int count = 1;
  int max = 5;
  int factorial = 1;

  while (count <= max)
  {
    factorial = factorial * count;
    count = count + 1;
  }

  std::cout << "factorial of " << max << " is " << factorial << std::endl;
}
```

This while loop calculates the factorial of the number stored in the integer variable `max`. You could easily modify this program to prompt the user for input and then calculate the factorial of the number the user input. We'd need to be careful if we did this because factorials get big really fast! If someone enters a number that is too big it won't fit in the factorial variable so the answer will be wrong. The max value that an integer can hold is 2147483647 but the factorial of 13 is 6227020800 which is too big. We need to validate the user's input and make sure they inter a positive number less than 13. We can use another loop to validate the input

```cpp
#include <iostream>

int main()
{
  int count = 1;
  int max = -1;
  int factorial = 1;

  while (max < 0 || max > 12)
  {
    std::cout << "enter a number between 0 and 12 ";
    std::cin >> max;
  }

  while (count <= max)
  {
    factorial = factorial * count;
    count = count + 1;
  }

  std::cout << "factorial of " << max << " is " << factorial << std::endl;
}
```

The new loop will keep asking the user for input while max is out of the acceptable range. If the user enters a number that is lower than 0 or higher than 12 the loop will run again and ask the user for input again.

One important trap to avoid is the infinite loop. Infinite loops occur when the condition can never become false. This can happen if you do not update the condition or if the condition will never be false even when updating it. Here are some examples of infinite loops. Try to identify the cause

```cpp
// infinite loop 1
while (true)
{
  std::cout << "infinite" << std::endl;
}
```

```cpp
// infinite loop 2
int count = 1;

while (count < 5)
{
  std::cout << "count" << std::endl;
}
```

```cpp
// infinite loop 3
int count = 1;

while (count < 5)
{
  std::cout << "count" << std::endl;
  count = count - 1;
}
```

The first loop is obviously infinite because the condition is always true.

The second loop is infinite because the `count` variable is not updated. Since `count = 1` and `1 < 5` is always true, the loop will run infinitely.

The third loop actually updates the count variable but it is subtracting from it. The first time the condition will be `1 < 5` which is true. Then it will be `0 < 5`, then `-1 < 5`, etc... As you can see, the condition will still always be false, therefore; the third loop is also infinite.

# For Loops

A for loop has a more complicated syntax but it is not hard to use. This is what it looks like

```cpp
for(initialization; condition; update)
{
  // code to run
}
```

Lets translate the factorial code into a for loop and look at the differences

```cpp
#include <iostream>

int main()
{
  int max = 5;
  int factorial = 1;

  for (int count = 1; count <= max; count = count + 1)
  {
    factorial = factorial * count;
  }

  std::cout << "factorial of " << max << " is " << factorial << std::endl;
}
```

The first part of the for loop is the **initialization** step. This is where you usually initialize the counter variable that you will use. You do this just like declaring any old variable `int count = 1;`.

Next is the **condition** step. This is just like the condition of the while loop. The for loop will evaluate this expression each time it loops and will stop when the condition evaluates to false. Just like in the while loop, we want to loop while `count < max`.

The last part is the **update** step. This happens at the end of each loop. It is used to update the counter. It is usually the line you would put at the end of a while loop to update your condition.

For loops are usually better suited for situations when you know how many times you need to run a loop. Like in the factorial, we know that we need the loop to go for a set number of times. `n` times to be exact when you are calculating `n!`. 

While loops are better suited for when you need to keep looping an unknown number of times until a condition is met. Like when we were validating the user input. We don't know how many times the user will enter invalid input. It could be once, it could be a hundred times. 

In the end, either kind of loop can be used for almost any situation. A way to know which loop to use is to think, do I need to keep repeating *while* some condition is true, or *for* a certain number of times?

# Challenge #4

Prime Numbers! This challenge is to write a program that will print out the first `n` integers. `n` should be input by the user when the program is run, then it should print out the first `n` primes starting with `1`. Example output could look something like this:

```
$ ./a.out
enter an number: 15
1, 2, 3, 4, 5, 7, 9, 11, 13, 17, 19, 23, 25, 29, 31,
```

To break up the task, try writing it in pieces. Determine if an arbitrary number is prime, if it is, print it out. Then keep track of how many primes you've found and keep going until you've found as many as the user specified. As always, if you have any questions, let us know!
