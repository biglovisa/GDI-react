# Get Started with Git

This is a brief guide on how to create a git repository, make a git commit and connect a git repository to GitHub. See resources at the end for git tutorials/articles.

All of the commands below should be run from the command line.

**Create a git repository**

Go to the root of the repository you want to be tracked with git. If you want the repository `Cats` to be tracked, when you run the command `pwd` in your terminal, it should return something like this: `some/path/to/Cats`. This command should only be run once.

```
$ git init
```

**Make a git commit**

After writing some code you would like to save, you need to commit it. Code that you write should be committed in small, logical chunks. Think of a commit as a bookmark in the history of your code, you can go back to it later if you need to.

Making a git commit involves two steps:

1. Choosing files to commit
2. Writing a commit message to describe the code to commit (for example: `Add contact form`)

Step one:
```sh
$ git commit fileToCommit.js
```

Step 2:
```sh
$ git commit -m "Add contact form"
```

**Connect git repository to GitHub**

If you want to push your changes on GitHub, you need to connect your local git repository with a GitHub repository.

Go to GitHub and create an empty repository. I usually name the GitHub repository the same as the local git repository. After creating the repository on GitHub, you'll see a screen where you can choose three different ways of finishing setting the repo up. You want the second option: `push an existing repository from the command line`. Run the two commands from the root of your local git repository.

To check if everything was set up correctly, check to see if the local git repository has a remote:

```sh
$ git remote -v
```

You should get something like this back:

```sh
origin  git@github.com:yourGitHubUsername/repoName.git (fetch)
origin  git@github.com:yourGitHubUsername/repoName.git (push)
```

## Git Resources

* [Official Git Tutorial](https://git-scm.com/docs/gittutorial)
* [CodeSchool: Learn Git](https://www.codeschool.com/learn/git)
* [Got 15 minutes and want to learn Git?](https://try.github.io/levels/1/challenges/1)
