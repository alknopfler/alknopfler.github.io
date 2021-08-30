---
title: "Rebase after Pull Request"
date: "2021-08-30"
categories: 
  - "rebase"
  - "pull request"
  - "development"
tags: 
  - "rebase"
  - "pull request"
  - "development"
  - "git"
---

# Situation
When you're working in your fork to make contributions to a open source project, you will usually have upstream and origin trying to represent the upstream (main project) and your origin (fork):

```git remote -v```

**upstream**: github.com/openshift/xx-project-xx

**origin**: github.com/alknopfler/xx-project-xx

In your fork you're working with a branch to develop a new feature that you want to contribute after to the upstream project:

```
git branch 

*my_branch
main
``` 

After you develop the feature, You've done a PR with your changes from cmd_platform to upstream, but inmediately you get:
![img](https://assets.digitalocean.com/articles/eng_python/PullRequest/conflicts.png)

# Rebase after Pull Request
There are few ways to solve the issue, but all of them basically use rebase to fetch the changes done before.

- In your project, change to main in order to pull from upstream into your fork main branch (basically update your main with last upstream changes)

```git checkout main ; git pull upstream main```

- Now, with the branch master/main updated, you need to change to your branch (my_branch)

```git checkout my_branch```

- Do the git rebase to main

```git rebase main```

- Now you could have several files with conflicts. So you could solve it, using the IDE to validate and solve the conflicts accepting yours or the current changes.
Usually you could follow the git instructions which in my opinion are quite useful with this task.

```git add/rm file```

- After conflicts solved you need to commit the changes and push "forcing" the changes to origin and your current branch. Automatically, the PR will be updated with the changes once done the rebase to get new changes updated.

```
git rebase --continue
```
When you finish to solve the conflicts:
```
git push -f origin my_branch
```
