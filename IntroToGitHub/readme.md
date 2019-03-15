# Git Hub Basics

### Git Commands

The following are very basic git commands that one should learn and use often!

```
git init
git remote add origin [main repository branch]
git add [item to add]
git status
git commit -m "very helpful comment!"
git push origin [branch you wish to push to]
git clone [git hub repo you wish to have a copy of]
git pull origin [branch name you wish to pull from]
git fetch
git branch
git checkout [branch name you wish to checkout]
git checkout -b [creates a new branch and switches to that branch]
```

Oof! That is a lot of things thrown at you at once! But that is okay! We will be using these commands plenty and they will soon be second nature to you! The key is always to practice! Let me break these commands down for you one by one.

```
git init
```

This initializes an empty repository! It tells the current directory that it will be used for version control and that it is a git repository. What is a repository? It's basically a folder/directory that lives in the cloud but has access to every single change and it's history that has been committed. It's pretty neat! 

```
git remote add origin [main repository branch]
```

This links the initialized git repository to the main branch of a git repository. Say online I create a new repository on Github. In fact, let's create one right now!

Go to https://www.github.com and sign in! (Technically, you are already signed in) In the top left section you should see your Username followed by repositories. Click `New`. You will now be directed to a new page titled: `Create a new repository`. You should see your username under `Owner` followed by a slash and a blank box. Name the repository: `MyFirstRepo`. You may choose to give it a description if you like. If you notice there is a `Public` and `Private` option. I must advise you, while putting homework on a git repo is totally the best thing to do. You should make homework repositories private so a classmate doesn't find your repo and steal your code! For this case, we can keep it public! Go ahead and click `Create repository` at the bottom.

You should now be on a page that shows your repository! But it's empty :( don't worry, we will fix that shortly! Notice the `Quick setup` section. There should be a web link that goes something like `https://github.com/[your username]/MyFirstRepo.git`. Go ahead and copy that link.

Now open up your terminal and navigate where you would like your repository to be. I always like my repositories to be in Documents. But feel free to choose which ever directory you like. If you need a reminder on how to navigate the terminal, go back to the `Navigating your terminal` and `Bonus Terminal` sections in the [Intro folder's readme](../Intro/readme.md). Once you are in your desired folder, go ahead and create directory called `MyFirstRepo` (`mkdir MyFirstRepo`). Change directories into your newly created folder. 

Verify that you are in your folder and that it is empty by listing the directory. (`ls` or `dir`). Once you have verified it, we are now ready to start! First, we must *initialize* the repository, we do that with the command `git init`. Your terminal should say "Initialized empty Git repository in [the directory you chose]." Great! Now we just need to link the repositories! And that is done with the command `git remote add origin [main repository branch]`. However, instead of `[main repository branch]` we will paste our code there. So it should look like: `git remote add origin https://github.com/[your username/MyFirstRepo.git`. Once you have done that press enter. And that's it! You have successfully linked your repository! Verify with the command `git status` (we will get to this soon) and you should see:

```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

```

If you don't, you have done something wrong! Check and make sure you copied the right link. If things are completely wrong, delete the folder and start again! :)

So now we have an empty folder with a link to a Github repository. Let us continue down the list as this will help us out in a little bit.

```
git add [item/s to add]
```

This basically adds the file/s that you would like to stage to the tracking area. Think about getting ready to cook a meal. You need salt, so you grab the container of salt and place it on the table next to the other ingredients that need to go in the recipe. That is what `git add` does. 

```
git status
```

This tells the user what the status is of the repository. It shows the state of the repository, what branch you are on, and what items are in specific staging areas. So back to the cooking, this is essentially verifying where all your ingredients are. Did you forget pepper? Do you thyme out?  

```
git commit -m "very helpful comment!"
```

This changes everything from your tracking stage to the commit stage. It is essentially the two tablespoons of salt the recipe called for. You have all the ingredients ready and you're ready to start cooking. It is the same here, you are ready to push your items to the branch.

```
git push origin [branch you wish to push to]
```

This is the final push. You are now ready to put all your ingredients together and you begin cooking. This will push everything in your commit stage into the branch of your choice.

Okay! So let us pick up where we left off. Go ahead and create a file called `myfirstcommit.txt`, and place anything in the file. I put `ples` but you can do whatever you want to do. Now place that file in the directory you created, or hopefully, you have created the file there anyways. Once you have finished, go back to your terminal and type `git status`. You should now notice that you have an Untracked file named `myfirstcommit.txt`. Well, let's go ahead and track it! Type `git add myfirstcommit.txt`. What happened? Well, type `git status` to find out.

Woah! Now we have something new, it says `Changes to be committed:` and you should see your file being tracked! Well, now we are ready to commit the file! So type `git commit -m "This is my very first Github commit"`. Hopefull you didn't skip the setup of your git in your terminal! If you did, you will be yelled at to say who you are, simply follow the instructions on your screen and you will be okay! 

Well now what happened? We have a file changed and insertions. Type `git status` (noticing a pattern here?) and see what happens. What happened? Well we have moved everything off our commit stage and it is simply waiting for us to push it. So now, we can go ahead and do `git push origin [branch you wish to push to`. We want to push this one to the master branch in this example. So we will type: `git push origin master`. If you are prompted for your username and password, go ahead and type those in. And bam! If everything went well you should have successfully pushed that file to your master branch! Go ahead and visit your repository online and you should see a difference!


# Take A Break!

Alrighty, now I have showed you the basics of github. From here, will be a little more complex and harder to follow. So take a short break if you need and when you are ready, let us go ahead and start!

### More Git command explanations

Well first what is a branch? I have said that more than once in this tutorial and I haven't said anything about it until now. Github repositories are trees. Where the tree is always growing but the `master` branch is the trunk of the tree always growing. General practice in working with team projects is to never touch the `master` branch. In fact our repository strictly forbids you to push to the `master` branch without creating a pull request! So we create branches, branches contain a copy of the `master` branch until we are ready to merge with master. 

```
git clone [git hub repo you wish to have a copy of]
```

This simply makes a copy from a repository online and stores it on your local machine. We will be using this very soon! 

```
git pull origin [branch name you wish to pull from]
```

This will update the current branch you are on if there are any updates needing to be made. Or it can merge one branch into the branch that you are currently in. Be very cautious of when using this. As this can overwrite files that you have not finished with and can cause merge conflicts! And those are not fun to clean up.

```
git fetch
```

This will update you repositories with all of the branches that lie within that repository. Occasionally, another developer will have their own branch. And maybe you need to make an update to their branch by merging your branch into theirs. Or simply need to update a peice of code. However, if you type `git checkout [their branch]`. Your local machine will not know that branch exists. So you solve this with `git fetch`. 


```
git branch
```

This displays the current branch that you are working on.

```
git checkout [branch name you wish to checkout]
```

This checks out a branch that we want to see. Developer A has a branch called `PatchFix34` and developer B has a branch called `ImplementFeature12`. Developer A approaches developer B and says, "hey man, I got something really wonky going on in my code, do you think you can checkout my branch and compile it on your computer to see if the same thing is happening?" So after developer B commits all of his changes to his `ImplementFeature12` branch, developer B then checks out developers A's branch after fetching the repository, he then runs `git checkout PatchFix34` and compiles developer A's branch. 

```
git checkout -b [creates a new branch and switches to that branch]
```

This command is used when we want to make a new branch and switch to that branch immediately. This will take a copy of the **current branch** you are on and will create a new branch.

### Piecing it all together

Now that you have an understanding of the commands we are ready to start doing some crazy stuff! Let us go ahead and create a new branch called `updateFirstCommit`. And we will do that by typing in our command line `git checkout -b updateFirstCommit` and press enter. If you succeeded, you will see "Switched to a new branch 'updateFirstCommit'". Well, let's go ahead and add another line to that file! I added: "I like food", do whatever you want to do though! Make sure you save and close this file. Now go ahead and run `add`, `commit`, and finally `git push origin updateFirstCommit`. Go ahead and scroll up if you need a reminder on how to add and commit files. **Make sure you close your text file**

Okay so now you have pushed your branch and your updated file to Github! You can verify this by going to your repositories main web page and there should be a notification with a recently pushed branch and the name of our branch. There is also a button that says, `Compare & pull request`, let us hold off on that button for now.

Now run `git checkout master`. On your terminal, you should see the notification that you have switched to the `master` branch. Go ahead and open your text file now. 

What happened?! Where is our second line that we added?! Relax! Everything is okay, the master branch is `behind` our `updateFirstCommit` branch. So it doesn't know that we have made any changes to it. This is a good thing, remember, we don't want to touch master very much. And any changes we make should be done on a separate branch. So let us go back to the web page!

Go ahead and click that `Compare & pull request` button. We are now directed to another page that says `Open a pull request`. It should be able to merge and should have a happy green check mark there. And your commit message should be displayed in the text box (did you remember to leave a helpful commit message?). If you would like to leave a comment, you are more than welcome to, comments are basically further clarification on your updates to your branch. Go ahead and click `Create pull request`.

You should now be directed to another page showing your pull request. Normally in a team environment, you will not be able to merge your own branch into master. Someone else will need to checkout your branch, verify everything is good, and then merge into master. However, for the educational value, we can go ahead and click `Merge pull request`, click `confirm merge`, and finally `Delete branch` (don't worry! This will not delete the branch on your local machine!). Now let's go back to our terminal. 

Type `git branch` to make sure you are on the `master` branch. Now, go ahead and type in your terminal `git pull origin master`. And you should see and update to your branch. Go ahead and open that text file again. Phew! Now we don't need to have a heart attack anymore. We can now see our newly updated line!

### You did it! 

Yay! We have finally made it here. You now have all the tools that you will need to at least get started on git. The only command we did not cover is `git fetch`, however that will come in time as you get going later. So give yourself a pat on the back and let's get ready to clone down the repository for the tutorial!

# Clone the CppTutorial repo

So here we are! In your terminal, navigate to a directory you would like to clone the C++ Tutorial. Once you are there go ahead and run `git clone https://github.com/Cubium/CppTutorial.git`. Once it is done downloading, run `ls` or `dir, and verify you have downloaded the directory. And that's it! We are done, return to the [Intro Tutorial](../Intro/readme.md) and continue from *Types in C++*
