

## Description

A simple sbt project to store git training material.

## Prerequisites

* GitHub account (with SSH configured)
* git (command line tool)
* Scala and SBT
* IntelliJ IDEA

## Stage 1 - create project and initialise git

Open a terminal window and run the following commands:
```
$ mkdir dev && cd "$_"    // Make a new directory and changes directory into it
$ sbt new sbt/scala-seed.g8   // Create a simple sbt project
```
You will be asked to enter a project name, enter a name and press enter. You should now have a new Scala sbt project in that directory. **Open this project in IntelliJ IDEA**. The template project has two main files we are interested in, Hello & HelloSpec
![[Pasted image 20230114181441.png]]
HelloSpec is the test class that tests the functionalities in the Hello class. Have a look at the single test in the HelloSpec class and see if you understand what it is expecting Hello class to do. Let's run the test now. Go back to your terminal and make sure you are in your new project's directory. Run the following command to execute the HelloSpec test:
```
$ sbt test
```
sbt will compile your project, look for any test files and run them all. You should see results similar to the following:
![[Pasted image 20230114181757.png]]

Let's initialise this as a git repository and push it to a git host. Run the following commands:

This will initialise your project as a git repository. After running the following command, if you look at your project in IntelliJ IDEA you will notice a new hidden directory called **.git**
```
$ git init
```
Git will now be able to see the state of your files and folders
```
$ git status
```
You will see results simillar to teh following:
![[Pasted image 20230114182037.png]]

git tells you that:
- You are currently on the branch called "main"
- You have not commited anything yet
- And you have some folders and a file that git is not tracking yet (they are untracked)

When you opened your new project in IntelliJ IDEA, it created a IDE specific folder called .idea that we don't want to include in the git repository since it is specific to our local IntelliJ setup and may cause issues for others when they clone our project. Git allows us to **ignore** such files and folders using a file called ".gitignore". Create this file in the root of your project and add .idea/* to it and save it. This will tell git to ignore all files in the .idea folder. Now if you run "git status" command again you will notice that .idea no longer shows as an untracked file but .gitignore is now tracked as it is a new file in your directory. 
![[Pasted image 20230114182408.png]]
Let's "stage" these project files. The following command will add these files to the staging area ready to be pushed to our branch (main branch). Run the folllowing command:
```
git add .
```
You will see an output simillar to the one below:
![[Pasted image 20230114183030.png]]
We should now leave a comment describing what we have changed and then commit these changes to your local branch (main). The following command will achieve this:
```
git commit -m "Create sbt project"
```
You will see output simillar to the following giving you a bit more info on what has been commited to your local **main** branch
![[Pasted image 20230114183758.png]]

Well done. You made your first commit.


# Stage 2 - create a GitHub repo and push your project

Let's create an empty repository on GitHub. Go to your profile on GitHub, click on the repositories tab and create a new repository.

![[Pasted image 20230114184559.png]]

Since you have already initialised your project as a git project in Stage 1 you need to run the commands in "... or push an existing repository from the command line" section. Let's see what they mean. 
![[Pasted image 20230114184849.png]]

The first command will add the address of where your local changes will be pushed to on github (i.e. the repository you just created there)
```
git remote add origin git@github.com:<your-github-username>/<your-project-name>.git
```

The second command will simply rename your branch to main (but yours is already called main so it wouldn't really do anythin in this case)
```
git branch -M main
```

The third and the final command will push your local changes to the remote repository's (upstream's) **main** branch.
```
git push -u origin main
```

Your output will look something like the following:
![[Pasted image 20230114190307.png]]

Congratulations. You have now pushed your changes to the remote repository. Navigate to your project on GitHub and you should see your proejct files there. 

# Stage 3 - Branches and  pull requests

# Stage 4 - Merge conflicts