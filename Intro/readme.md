# Intro to Git, installing C++, and Hello World!

Greetings! You are now stepping into the wonderful world of Git and C++! Git is an essential tool for all developers and it is very important that you become proficient with this tool. If you already know Git, go ahead and jump down to the [Hello World!](#hello-world!) Section below!

## Setting up Git on your Machine

### Linux Users:

This is rather easy for Linux users. I will assume Ubuntu as the operating system for this setup, but it is as simple as running `sudo apt install git`. Once you are done with that, you will just need to set your credentials by running the following commands in your terminal:

```
  git config user.email "your email (quotes not necessary)"
  git config user.name  "your github username"
```

And that's it! You're done! Now let us move on to the next task.

### Mac Users

For OSX Users, it will be easiest to install Homebrew. Open up your terminal, if you do not know how to open it. Simply open your spotlight `command + space` and search terminal. Once you open up your terminal insert the following commands:

```
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  brew doctor
```

You will be asked if you want to install Command Line Developer Tools from Apple. Click install and follow the on-screen prompts. Once that is finished installing, simply run `brew install git` (Note, if brew is not recognized, close your terminal and open a new instance of it) and git will be installed. Next, you will need to set up your credentials with the following commands in your terminal:

```
  git config user.email "your email (quotes not necessary)"
  git config user.name  "your github username"
```

And that's it! You're done! Now let us move on to the next task.

### Windows Users:

Simply visit the website: https://git-scm.com/download/win (A download will automatically start, however, you may cancel this automatic download and download the 64 bit version should you wish to install that version instead.

Next, you will want to run the executable. Click `Next` until you arrive to the `Adjusting your PATH environment` option. Select `Git from the command line and also from 3rd-party software`. Continue to click `Next` until you you arrive to the `Configuring the terminal emulator to use with Git Bash` and select `Use Windows' default console window`. Click `Next` and when you arrive to the install screen. Simply press `Install` and you are done.

Next, we will need to open up a terminal to set up your credentials. Simply in your search bar, type `CMD` and press return. Once you are in your terminal, set up your credentials as follows:


```
  git config user.email "your email (quotes not necessary)"
  git config user.name  "your github username"
```

And that's it! You're done! Now let us move on to the next task.

# Installing C++

### Linux Users:

This again is as simple as typing `sudo apt install g++` and all of the C++ libraries will be installed on your machine. To verify installation, type `g++ --version` and the latest version should appear on your screen.

### OSX Users:

This you will need to have XCode Installed. In your App Store, search for XCode and follow the installation instructions for XCode and the XCode Command Line Tools. To verify that you have C++ installed on your system, open up a terminal and type `g++ --version` and the latest available version should appear on your screen."

### Windows Users:

For this installation, you can install Visual Studio 2017 and install the C++ functionality and you are done with it. However, I highly encourage you to install MinGW as well. Especially if Visual Studio is not an option for you. 

Navigate to the website: https://mingw-w64.org/doku.php/download/mingw-builds. Download the executable from the sourceforge link and run the executable. You will be directed to a screen that has Version, Architecture, threads, etc. This looks intimidating and scary, however what you need to focus on is the `Architecture`, if you need the 32-bit for your computer, leave it at `i686`. If you need the 64-bit version, select `x86_64` from the drop down menu. 

Click next and let MinGW install in the default location, you may change this install location if you wish. Click next to install. Click finish and follow the next set of instructions.

In Windows 10, on your search bar, search for `This PC`, right click on `This PC` and select `Properties`. In the top left section, you will see an option called `Advanced system settings`, click on it. You will see a new window open, towards the bottom of that window select `Environment Variables...`. You will then see your `Environment Variables`. We need to add `C++ bin's` to our `Path` in order to be able to compile any C++ code. This is also required to do for CLion. Click on `Path`, once `Path` is high lighted, click on `Edit...`. This is where you will add the `bin` of C++. Click `New` and then click `Browse...`. Depending on your install version (32 bit vs 64) you will need to go to where the folder installed. For me it was in `This PC` -> `C:` -> `Program Files` (this could be Program Files(x86) if you installed the 32 bit version) -> `mingw-w64` -> `x86_64-8.1.0-posix-seh-rt_v6-rev0` -> `mingw64` -> `bin`. `bin` is the folder you want to click on, then click `ok`. Then click `ok` until you get to the original `Properties` page.

Next, open up your terminal. Close the one you had open previously since we need to reload the path variables. Next type `g++ --version` to verify that you have successfully installed C++ as the latest version should appear on your screen.

# Hello World!

In C++ there are two different type of files, `.cpp` and `.hpp`. The first file type, commonly known as a source file, has the extension `.cpp` for C Plus Plus. The second file type is known as a header file with the extension `.hpp`. For your first Hello World program we will only use a single source file (`.cpp`).

In your favorite text editor or integrated development enviroment (IDE), like Visual Studio, CLion or XCode, start a new project and call it HelloWorld. If you are using a text editor and the commandline create a new folder titled HelloWorld and file called `hello.cpp`. In this tutorial I will focus on compiling code on the command line. Getting familiar with the command line is important and it will make you a better developer to know what is going on under the hood!

Type the following snippit into `hello.cpp` (which I encourage the most), don't copy and paste, you'll write bugs, every, single, time!

```cpp
#include <iostream>

int main()
{
  std::cout << "Hello, World!" << std::endl;

  return EXIT_SUCCESS;
}
```

### Navigating your terminal

I will assume that if you are a Linux user, you will know how to navigate the terminal on your own. However here are a few basic commands that you should know!

Linux/OSX Users
```
cd "Change Directory"
ls "List Directory"
rm "remove"
mkdir "Make Directory"
```

Windows Users
```
cd "Change Directory"
dir "List contents in Directory"
del "Delete"
mkdir "Make Directory"
```

### Compiling Hello, World!

Open up your terminal and navigate to the location of `hello.cpp`. (Note: If you are using Visual Studio or XCode this section can be skipped, however, I highly encourage you to follow along to learn more about the command line!) If you are using VS/XCode simply build and run the project and skip to the [Explanation of the Code](#explanaiton-of-the-code) section. 

How do we navigate? For example, say my `hello.cpp` is located in `Documents`. Well, how do we know where we are? In Windows, we have a handy bar that shows our location. If it reads: `C:\Users\YourUserName` then we know that we are in the C Drive, Users, and our specific folder! Well now we want to be able to *change directories*. In Linux/OSX type `ls` to display the contents in the directory we are in. In Windows, type `dir`. You should see a bunch of stuff on the terminal screen. What is it? This is the contents of the current directory you are in. You should see `Documents`, `Downloads`, `Pictures`, etc. Well we want to *change directories* into `Documents`. So in order to do that we will type in the terminal:

```
cd Documents
```

If successful, we should have changed our directory into `Documents`, type `ls` or `dir` to confirm that you are indeed inside `Documents`. If we are, great! We have successfully navigated to `Documents` folder and we should see our `hello.cpp` in the directory. 

Now we simply need to compile our program! And that is just as easy as typing `g++ hello.cpp`. Type `ls` or `dir`. In Linux/OSX you should see a `a.out` and in Windows you should see an `a.exe` executable. How do we run our compiled program? In Linux/OSX we type `./a.out` and in Windows we type `a.exe`. And you should see a happy, Hello, World\! on the screen!

### Bonus Terminal

Now that we have compiled the code and successfully ran it. We should explore navigating in and out of your terminal a bit more. Since we are in `Documents` why don't we go ahead and create another folder called `Foo`. Simply type `mkdir Foo` and then *list the directory*. You should see the newly created Folder `Foo` in `Documents`. Now go ahead and *change your directory* into Foo. Now *list the directory*. What happened? You should see nothing listed on your screen! Because we have just created an empty folder called `Foo`. 

How do we get back to our `Documents` Folder? Well, it's actually really easy. To go back a directory or back to the parent folder, we simply type `cd ..` so go ahead and try it and then *list the directory*. Where are you now? You should be back in your `Documents` Folder! Go ahead and play with that a couple of times. Type `cd Foo`, `ls` or `dir`, `cd ..`, `ls` or `dir` and make that a habit! 

### Explanation of the Code 

Okay so what exactly happened in our code? There are probably a million questions running through our heads but that is okay! We will start from the Top!

C++ is top down code, meaning the compiler starts from the very beginning of the source file and checks every single line of code you have written until you have reached the bottom! So we will start at the first line

```cpp
#include <iostream>
```

This is telling the compiler, I want to include the iostream (input/output stream) library. Whenever we want to interact with the user (print or read from the console), we must include this library. The way we include libraries is `#include`. (Pound Include, not __hashtag__ include!). Let's move on to the next line:

```cpp
int main()
```

This is arguably the most important piece of code in this entire file. This is our main driver, the ignition to our car, the power button to the TV. Every C++ program must have a main function in order for it to run, it is where the program starts running. Every C++ program will have `int main()` in its code, it's required. Let's move on to the next line:

```cpp
{
``` 

This is important! And I put this in a single line because every function or method within C++ starts and ends with curly braces. This is known as a scope and a `{` opens a new scope. When we put the scope together we have something like this:

```cpp
int main()
{ // beginning of scope

} // end of scope
```

Every curly brace, every parenthesis, and every bracket will have a closing one associated with it. However each function will have a scope. Now let us move on to the next line:

```cpp
  std::cout << "Hello, World!" << std::endl;
```

Wow! What a mouthful that statement is! Knowing the output of the file, you're probably thinking, "That is what I have to do in order to print something out to the console?!" And the answer is yes! But let me tame this scary statement and put it into a readable sentence let us start with `std`. `std` simply means the standard library (not S.T.D's!!). The `::` tells the compiler where to look for the following thing, in this case `cout`. So now let us look at `cout`, this stands for Console Out. So let us put that all together, `std::cout` means, "In the standard library, use Console Out".

Next let us look at `<<`. I have always called these things waka-wakas, like the sound Pac-Man makes. However, their official name is actually the stream insertion operator. You use `<<`'s to put things onto `cout`. I like to remember it like arrows pointing to which way the information is going, towards the `cout`.

Now let us look at `"Hello, World!"`. This is a string, you can change this string to whatever you want to change it to! Go ahead and experiment. And yes, every string begins and ends with quotations. 

So let's put that whole line together `std::cout << "Hello, World!"`. This simply reads, "In the standard library, use Console Out and insert the string "Hello, World!" onto it." Great! Now we just have one final piece to look at!

`std::endl`, well you already know what `std::` means, so all we have to decipher is the `endl` part. And it's actually really simple! It means End Line. This tells the `cout` stream that we are ending the line there and anything after that will need to be on a new line. So let us put it all back together!

`std::cout << "Hello, World!" << std::endl;` This simply reads, "In the standard library, use Console Out and insert the string "Hello, World!" onto it. Then in the standard library, use the end line.

Now there is one tiny little guy that I have ignored but will finally address. `;` <--- The semi-colon is equivalent to the period in English. We end each of our statements with a semi-colon. Now that we have covered that big thing, let us go ahead and move on to the next line of code!

```cpp
  return EXIT_SUCCESS;
```

This line is our programs way of telling the operating system "I have successfully finished running". Now the final bit of code:

```cpp
}
```

This closes the scope of the program and now the compiler knows that we have reached the end of a function. So always keep in mind that every beginning of a scope must have an end to a scope.

# Take a Break!

If that was a lot to dive into, take a break! Browse some of your favorite memes, watch a show, or distract yourself with something fun. The next section will be diving into the semantics of C++.

# Do the Git Tutorial

Before we continue, we must learn about git and how to use it. So [Click Here](../IntroToGitHub/readme.md) to be taken to the Git Hub Tutorial. Come back here where you are finished!

# Challenge #1

Navigate to the CppTutorial repository and in your command line create a new branch with your name as the branch. For example, `git branch Raul` then `git checkout Raul`. Or you can combine them and do `git checkout -b Raul` (I'll get to what this means at the bottom). Obviously replace Raul with your own name. 

Create a new directory within the directory named `Submission` and name it challenge1. Then create a C++ source file in the `challenge1` directory and name it `hello.cpp`. 

Get your hello world program to compile and run inside the new directory. Then play around with changing and adding more strings. You can chain the `<<`'s together like this `std::cout << "Hello" << "World" << std::endl;`.

# Pushing to GitHub

When you are ready to push your submission to github you will need to open up your command line and navigate to the CppTutorial directory, Submission, challenge1. Remember the basic rules of pushing up to Github are as follows: add, commit, push.

So when you are ready, you will type in your command line: `git add hello.cpp`. This will add `hello.cpp` to the queue of files to be committed. Next, you will type `git commit -m "Leave a helpful comment here"`. This means, I am committing this file and this is my reason why. Replace the Leave a helpful comment here with an actual comment such as. "I have finished the first challenge." Finally, type `git push origin yourBranchName` in this case, I would do `git push origin Raul`.
