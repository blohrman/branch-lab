# Lab: Branching

## Introduction

Up until now, everything you've done with git has revolved mainly around the actions of **committing** and **pushing**. These are the main two actions that one generally does with git, and understanding these is a great first step in understanding the compex tool that is git! However, there is another important facet of git that you will run into in internships and the workforce in general, and in this course we wanted to introduce you to it.

Today you will learn about **branching**. Let's get started!

## `main` and `master`

Within your previous repositories in RAIK 183H (last semester's class with Dr. Val), you may have noticed that, in GitHub Desktop, whenever you would commit it would say `Commit to master` or `Commit to main` at the bottom of the screen when you clicked the button to commit. This is the primary branch that nearly every repository has. This branch is the "source of truth" in a sense, and whatever the latest commit on `main` is contains the current tested, working, production code for whatever software contained in the repository.

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

## Branching from `main`

Remember that our `main` branch currently looks like this, with 5 commits:

```
a---b---c---d---e
```

In order to start developing our new feature, we want to create a new branch from `main`, which means we are going to essentially:

1. Copy the commits up to the point where we create the new branch.
2. Tell git that, when we commit and push on this new branch, it should not plop it on top of `main`, but rather on top of our new branch.

For a visualization, assume we've created a new branch after commit `e`, and then added a new commit `f` onto our new branch. This is what our repository now looks like:

```
                  f
                 /
a---b---c---d---e
```

Commit `f` is now on our new branch, but importantly **not** on `main`. Now we can continue developing without worrying about messing up our perfectly good code!

## You Try!

Whew, okay. That was a lot of information, and it can get pretty complicated pretty quick. So, let's practice!

1. Clone this repository!
2. Open the code in Eclipse, and run the main method. It should just print something to the console.
3. Open GitHub Desktop and navigate to the repository for this lab. You should see something that looks like this:
<img width="958" alt="Screen Shot 2023-01-25 at 12 06 23" src="https://user-images.githubusercontent.com/54636027/214646423-7430bc0e-c922-4d8a-b590-9e7359f4d3d0.png">
4. At the top, notice the dropdown that says `Current branch main`. Click this dropdown and you should see the following:
<img width="375" alt="Screen Shot 2023-01-25 at 12 12 25" src="https://user-images.githubusercontent.com/54636027/214647605-c969ff3a-7241-4afa-b955-fd0a79e8105a.png">
