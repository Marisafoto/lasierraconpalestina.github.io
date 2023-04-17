---
layout: page
title: Introduction to git and GitHub Pages
redirect_from:
  - /tutorial-git.html
  - /tutorial-git
---
# Intro to Git

This is meant to be a quick introduction to Git, GitHub, and particularly its use for creating and contributing to GitHub Pages. The Internet is full of amazing resources to learn this stuff, and I do not expect to do a better job here. This is just for me to be used when I teach it to others. Examples of resources online are the [official _try_ page on Github](https://try.github.io/) and the page [Git for collaborative documentation](https://cassgvp.github.io/github-for-collaborative-documentation/) by [Cassandra Gould van Praag](https://www.win.ox.ac.uk/people/cassandra-gould-van-praag), with whom I once did one tutorial. I will take a lot of inspiration from her here.

## What is Git?

Git is a [version control system](https://en.wikipedia.org/wiki/Version_control) (VSC)---another example of VSC is Subversion or SVN, which allows to efficiently manage the changes to software, websites, documents, etc. For example, by using a version control, it is possible to go back to older versions of the code or document, work on new features without touching the _official_ version and, crucially, collaborate with distributed teams.

GitHub (Github, Inc.) is the company---now a subsidiary of Microsoft, sadly---that manages and provides the internet service around Git. GitHub Pages is a [_static web hosting service_](https://en.wikipedia.org/wiki/Static_web_page) offered and hosted by GitHub.

## Why learning and using Git?

This would make a long list, so let's name just a few reasons:

* To enable version control in our projects
* To collaborate with fellows
* To release and open source the code of our projects. Open Science!
* To create websites with GitHub Pages

## Basic commands and flow

Git is a really powerful and flexible tool, which means that learning and understanding everything it offers can be complicated. However, the basic functionality is relatively simple. My recommendation to someone learning Git for the first time would be to first learn the basics superficially, practice with dummy repositories---as this tutorial will show---and later on making the effort to understand the details in more depth. Challenges will certainly arise as we use it in real applications, and these will be learning opportunities.

### Installation

First things first. Let's make sure to have git installed on our machine. We can follow [this instructions](https://github.com/git-guides/install-git) to install it on different operating systems.

### Repositories

Before looking into the commands, it is important to know the concept of a _repository_, which is central. We can think of a repository as the collection of files and directories that are part of a project. In a computer, a repository would be associated to a directory or folder. Repositories are linked to URLs, and they can be public or private.

### 1. Create a new repository

Let's go hands on! Assuming you have a GitHub account, log in into your account, click on your avatar and go to _Your repositories_. Then, click on _New_, write a name for your repository---I will use `my-repo` throughout this tutorial---and finally click on _Create repository_. You will see a page with some instructions on how to proceed, but let's go step by step. 

For now, copy the (HTTPS) link below _Quick setup_. For me, it is `https://github.com/alexhernandezgarcia/my-repo.git`

### 2. `git clone` the repository

Now let's open a terminal, change directory to the location where you want to download the repository, clone it, and change into the new directory containing the repository:

```
cd ~/
git clone https://github.com/alexhernandezgarcia/my-repo.git 
cd my-repo
```

### 3. Create the first file

Let's create a dummy file named `README.md`. You can either create it in your favourite way with your favourite editor, or do it from the command line. For example:

```
touch README.md
echo "The README file of my repository" > README.md
```

### 4. `git status`

Now we have done our first change, we can run `git status` to see _what_ has changed. It is a good practice to run this command often, especially during the learning phase, to keep track of what is going on in our repository. You will see that `README.md` appears below _Untracked files_, because we haven't added it to the repository. Let's do that!

### 5. `git add`

_Adding_ a file means to _stage_ a change, in Git's vocabulary. It can be seen as a pre-step to _really_ adding the changes to the repository. This may sound complicated now, but there are good reasons for it, that you may want to learn later. Adding a file is as simple as:

```
git add README.md
```

Now run `git status again to see what changed. Now `README.md` is under _Changes to be commited_. What does that mean?

### 6. `git commit`

Now we could continue working, adding more changes, perhaps in other files, and eventually we would like to _commit_ our changes to the repository so that the version control can keep track of them. _Commiting_ changes means to save a snapshot of the current state of our repository, with a time stamp and all the necessary things that will allow us to go back to this point in the future, and many other important possible actions. To commit our changes, we have to add a message describing the changes. This is the syntax:

```
git commit -m "first commit, add README file"
```

You may want to run `git status` again.

### 7. `git push`

All we have done now has been local, meaning that we have not yet posted our changes online so that others or ourselves can access it. We could continue working and adding and committing our changes, or we can _push_ the history of our changes now. The default way of pushing is simply:

```
git push
```

You may be asked for your username and credentials at this point.

Now the repository should be online! Go to your GitHub account and look for the URL of your repository. In my case, it is `https://github.com/alexhernandezgarcia/my-repo`

### 8. `git pull`

You have pushed your changes to the repository, and so may be doing your collaborators in a real application. If you want to _download_ the current state of the online repository, alongside its history, you have to _pull_ it:

```
git pull
```

It's good practice to pull the repository often enough, especially before commiting our changes. As a matter of fact, we will not be able to push our changes if our working directory is not up to date and Git will raise a warning.

## Branching

Branches are a really important concept in Git. Branches allow us to keep the development of a project well organised, especially if more than one person is working on it. Every branch can be seen as path in which the project is developing. For example, one person may be working on the content of a website and would create a branch `content` for that; and another person may be working on changing the background colour and work on branch `background`. It is possible that some branches end up dead, not being useful for the project, and that's fine as long as they live indeed in separate branches. Usually, there is a branch to rule them all and it is typically called `main`. In GitHub pages, for instance, what we see online in the URL is the version of the branch `main`. At any point, the code in one development branch can be _merged_ into `main`.

[Learning git branching](https://learngitbranching.js.org/) is an interactive online tool for learning about branching and practising the concepts.

Let's see how all this works by playing with the website of [USS 2021](https://uss2021.github.io/).

### 1. Clone the repository

The repository of the USS 2021 website lives in `https://github.com/uss2021/uss2021.github.io`. You can access the cloning link but clicking on _Code_. As before, go to the location where you want to download, clone it and change into the new directory. You can give a name to the folder by adding it to the `clone` command after the link. I will call it `uss-playground`:

```
cd ~/
git clone https://github.com/uss2021/uss2021.github.io.git uss-playground
cd uss-playground
```

### 2. Create a new branch

You can always check which branch you are on with `git branch`. And this is the command to create a new branch `my-branch`:

```
git checkout -b my-branch
```

Run `git branch` again to check how things changed.

### 3. Make some changes, add, commit and push

I have created _playground_ pages for each of you in the directory `_playground_`. You change directory into it to see the files and see the result online in `https://uss2021.github.io/playground/<filename>/`, for example [uss2021.github.io/playground/alex/](https://uss2021.github.io/playground/alex/).

The playground files contain a small introduction to Markdown. Feel free to change anything there; then `add`, `commit` and `push` the changes, as before.

```
cd _playground
<change your-name.md>
git add your-name.md
git commit -m "I played in the playground"
git push
```

It is possible that `git` may _complain_ because "the current branch has no upstream branch". That means that we have not yet set the _upstream_ branch---the location in the online, shared repository. If this is the case, it is safe to follow `git`'s suggestion:

```
git push --set-upstream origin my-branch
```

### 4. Pull request

The changes we have just pushed belong to a separate branch `my-branch` that we created at the beginning in order to avoid working directly on the `main` branch. Whenever we are ready to incorporate our changes to the `main` branch, we can do it through a _pull request_. A pull request opens the process to merge one branch into another. Typically, after a pull request is open, someone in the team will review the changes to be merged, discuss potential issues and eventually merge the branches.

To open a pull request, we can go to the URL of the repository on [GitHub](https://github.com/uss2021/uss2021.github.io), click on "branches", and on the right hand side of the branch we were working on under "Active branches" we can find "New pull request". In the next page, we have to make sure to correctlyset the desired "base repository" and branch---the target repository and branch to which we want to merge our branch---and "head repository"---the repository where we made our changes. We can further give a name and description to the pull request, and set the suitable revieweres so that they get notified.

If the reviewers approve the pull request an merge it, our changes will become part of `main` and, if the project is a GitHub page, we will see our changes online!

## To know more

### `git diff`

A very useful `git` command is `git diff`. It is very versatile, but one of the simplest use cases is the following:

```
git diff myfile
```

This will highlight in the terminal the parts of `myfile` that are different with respect to the last version.

### Forking

In the example above about branching, the workflow was `clone` &rarr; `branch` &rarr; `edit` &rarr; `push` &rarr; `pull request`. This will only work in the case we are _collaborators_ of the target repository. In general, we cannot `push` our changes to repositories we do not own, even though we create a new branch. This is the general case, typical of open source projects, for example. In this case, the workflow is slightly different: Instead of directly cloning the original repository, we have to first _fork_ it to our GitHub account. A fork is a copy of a repository at a particular moment of its development history. This is the beauty of open source projects: anyone can fork an open repository and continue the development of the project. After a fork, the new version may follow a completely separate path, and become a new project---for example, the website of USS 2021 was initially forked from [alexhernandezgarcia.github.io](https://alexhernandezgarcia.github.io/)---but it is also possible to create pull requests between forks, therefore merging features from one project into each other.

In this case, the workflow is the following:

1. Fork the repository you are interested in into your account.
2. Clone the forked repository into your computer.
3. Push changes into your copy (fork) of the repository. You can do this because you own your copy.
4. Open a pull request to merge your branch into the original repository.
5. Wait for the reviewers to review your changes, discuss possible issues, and merge into the target repository.

