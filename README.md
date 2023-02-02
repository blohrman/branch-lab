# Lab: Branching and Pull Requests

## Introduction

Up until now, everything you've done with git has revolved mainly around the actions of **committing** and **pushing**. These are the main two actions that one generally does with git, and understanding these is a great first step in understanding the compex tool that is git! However, there is another important facet of git that you will run into in internships and the workforce in general, and in this course we wanted to introduce you to it.

Today you will learn about **branching**. Let's get started!

## Part 1: Branching

### `main` and `master`

Within your previous repositories in RAIK 183H (last semester's class with Dr. Val), you may have noticed that, in GitHub Desktop, whenever you would commit it would say `Commit to master` or `Commit to main` at the bottom of the screen when you clicked the button to commit. This is the primary branch that nearly every repository has. From now on, I will refer to this branch as `main`, as that is the generally accepted term for it now. This branch is the "source of truth" in a sense, and whatever the latest commit on `main` is contains the current tested, working, production code for whatever software contained in the repository.

As a visual, say `main` looks like this, where `a`, `b`, `c`, and `d` are all commits:

```
a---b---c---d
```

When you add a new commit, call it `e`, and push it up to GitHub, it looks like this:

```
a---b---c---d---e
```

All that's happening is you add the commit on top of whatever the latest commit is. You've already done this plenty of times! However, consider the following scenario.

A new feature is requested for our product, but we don't want to push unfinished, unreviewed code directly to `main`. What do we do? The answer would be to create a **new** branch!

### Branching from `main`

Remember that our `main` branch currently looks like this, with 5 commits:

```
a---b---c---d---e
```

In order to start developing our new feature, we want to create a new branch from `main`, which means we are going to essentially:

1. Copy the commits up to the point where we create the new branch.
2. Tell git that, when we commit and push on this new branch, it should not plop it on top of `main`, but rather on top of our new branch.

For a visualization, assume we've created a new branch after commit `e`, and then added a new commit `f` onto our new branch. This is what our repository now looks like:

```
                  f   <- new branch
                 /
a---b---c---d---e     <- main
```

Commit `f` is now on our new branch, but importantly **not** on `main`. Now we can continue developing without worrying about messing up our perfectly good code!

### You Try!

Whew, okay. That was a lot of information, and it can get pretty complicated pretty quick. So, let's practice!

1. Clone this repository!
2. Open the code in Eclipse, and run the main method. It should just print something to the console.
3. Open GitHub Desktop and navigate to the repository for this lab. You should see something that looks like this:
<img width="958" alt="Screen Shot 2023-01-25 at 12 06 23" src="https://user-images.githubusercontent.com/54636027/214646423-7430bc0e-c922-4d8a-b590-9e7359f4d3d0.png">

4. At the top, notice the dropdown that says `Current branch main`. Click this dropdown and you should see the following:
<img width="375" alt="Screen Shot 2023-01-25 at 12 12 25" src="https://user-images.githubusercontent.com/54636027/214647605-c969ff3a-7241-4afa-b955-fd0a79e8105a.png">

5. Click the button that says `New Branch` and enter a name for your new branch. In general, try to keep branch names short, and separate words in branch names with dashes (`-`) or underscores (`_`). I named my branch `test`, but you're free to name it whatever you'd like!
6. Now, click `Create Branch`. You'll be greeted with a screen that looks like this:
<img width="962" alt="Screen Shot 2023-01-24 at 14 11 37" src="https://user-images.githubusercontent.com/54636027/214678115-a34d6a87-d519-4694-937c-fe0470d96626.png">

7. Go ahead and publish the branch! This is essentially like pushing a commit; it tells GitHub, "Hey! Here's a new branch! Please keep track of it for me!"

Notice that now your current branch is no longer main. You've successfully created a new branch, congrats!

8. Now, go back to Eclipse and edit the print statement in the given Java file to include the name of the branch you created rather than `main`. Once you've done this, go ahead and commit and push! Make sure that GitHub Desktop says your current branch is the branch you created rather than `main`!

Congrats, you're done with Part 1!

## Part 2: Pull Requests

### Getting New Code into `main`

Awesome! We now have a new branch containing updated code. That's cool and all, but what if we want to put this code into `main` so that our "source of truth" can reflect these new changes? For this task, we'll use what's called a **Pull Request**.

A pull request is a feature specific to **GitHub**, not git itself. Its purpose is to make sure that code gets reviewed properly before it can be put into the main branch, ensuring that multiple people look over the new additions and approve the changes. When you create a pull request, it shows what's changed between the time that you created the new branch and the time of the pull request. This makes it very easy for reviewers to see your changes and comment on them.

This is the tool that we will be using this semester to give you feedback on your code, rather than Gradescope. It will allow us to much more easily see your changes, comment on your changes, and let you see feedback in a more user-friendly way. Plus, it's how code feedback works in the real world!

### Let's Make a Pull Request!

So, in the last part, you pushed a commit to your new branch. Let's go ahead and make a pull request to put that change on `main`!

1. Open GitHub in your web broswer of choice, and navigate to your repository for this lab.
2. Take a look at the tabs near the top of the screen. One of them should say `Pull Requests`. Go ahead and click on that tab!
![Screen Shot 2023-01-25 at 14 22 17](https://user-images.githubusercontent.com/54636027/214681853-290d1abc-6b68-4300-b09c-01c51324e9c6.png)

3. From this new screen, click the green button in the top right that says `New Pull Request`.
<img width="1222" alt="Screen Shot 2023-01-24 at 14 14 56" src="https://user-images.githubusercontent.com/54636027/214682113-8dd722e0-a823-4552-8fc4-97edcb041658.png">

4. On this creation screen, it will prompt you to choose which branches to compare. The branch on the left side is the "base" branch, or the branch that you want to put your changes onto. The branch on the right is the branch with the new changes. For us, the "base" branch is `main`, and the branch to compare is the new branch we created, which is `test` for me!
<img width="739" alt="Screen Shot 2023-01-24 at 14 15 16" src="https://user-images.githubusercontent.com/54636027/214682449-94e9e949-4bb8-49af-8459-d625cfb10c77.png">

It should say "Able to Merge" in green, indicating that there are no **conflicts** with the base branch (if this is somehow not the case, raise your hand for help). This means that nothing in the base branch has been changed that has also been changed in the new branch. If this is the case, there is a **merge conflict** that needs to be resolved, because git does not know which version of the code you want to use, the version on the base branch, or the version on the new branch. This is a concept that you shouldn't need to worry about for this course, but it is useful to know for the future!

5. Click the button that says `Create Pull Request`. This should take you to a new screen that prompts you to enter a description for your pull request. In this section, you would describe a summary of the changes you've made to the code for anybody that goes to review your pull request. For our purposes, you can simply write something like "Updated print statement" and create the pull request.

Awesome! You've now created a pull request! The webpage should now look something like this:
<img width="940" alt="Screen Shot 2023-01-24 at 14 20 39" src="https://user-images.githubusercontent.com/54636027/214684150-5237f84f-a74c-47d3-a2e5-28f441b65327.png">

And if you click on the `Files Changed` tab, you should see something like this:
![Screen Shot 2023-01-25 at 14 34 31](https://user-images.githubusercontent.com/54636027/214684261-77f8a333-2b78-4e29-8cfb-ad3715c2a390.png)

Wow! You can see exactly what you've changed, leave comments on it, review the code, see the commit history, and several other nifty things. How cool is that!?

Once people have reviewed your code, the button that says `Merge pull request` will be used to take the code on your branch and plop on top of the base branch, and your code will be in "prod"! For now, leave the pull request un-merged so that we can see you've completed the lab easily. Nice job!

## Wrap-Up

Awesome, you've completed all the tasks that we had for you to do in today's lab. Tomorrow is when the first "feedback" submission for PacMan occurrs. The pull request has already been created for you, but now you have an understanding of what's going on! Note that **ONLY COMMITS MADE BEFORE THE DEADLINE WILL BE REVIEWED!** We can see commit times, and pushing late **will** cause any commits you forgot to push before the deadline to not be counted! **PLEASE MAKE SURE YOU COMMIT AND PUSH BEFORE THE DEADLINES THIS SEMESTER!**

Thanks for coming into lab today! Have an awesome day and weekend!
