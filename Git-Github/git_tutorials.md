# **Git & Github**

## **Listing local & remote branches**
```bash
# list all local branches
git branch

# list all remote branches
git branch -r

# list all branches including local & remote
git branch -a
```
This command lists all branches stored on the remote, prefixed by the remote name (e.g: `origin/feature-branch`).

## **Creating a new branch**

1. To create a new local branch, use the following command:

    ```bash
    # syntax
    git checkout -b <branch-name>
    # example
    git checkout -b feature1
    ```

2. To create the copy of the branch in the remote repository:

    ```bash
    # syntax
    git push <remote-name> <branch-name>
    # example
    git push origin feature1 
    ```

3. Or to set an upstream branch, so that a subsequent git pull will know what to do, you might instead want to use:

    ```bash
    # syntax
    git push --set-upstream <remote-name> <local-branch-name> 
    # example
    git push --set-upstream origin feature1
    ```
    The above command creates a remote tracking branch

## **Pull changes from a remote branch**

1. Checkout to the feature branch into which you want to pull and merge the latest changes.

```bash
git checkout <branch-name>

# alternatively
git switch <branch-name>
```
If the branch doesn’t exist locally, you can 
fetch and check it out in one command. The below command creates a new local branch tracking the remote branch:
```bash
git checkout -b --t feature-branch origin/feature-branch
```
The option `-t` or `--track` specifies to track the remote branch and is optional

2. Fetch all the data from the remote repository. After fetch you will have references to all the branches in remote.
```bash
# fetch the latest changes for the currently checked out branch
git fetch
# fetch data from all the repositories
git fetch --all

# or fetch info from a particular repo
git fetch <remote-name> <branch-name> # syntax
git fetch origin main # example
```
## **Best Practices for Pulling Remote Branches**
- Regularly pull changes from the main branch to keep your work up-to-date and reduce conflicts.
- Use git fetch to review changes before integrating them.
- Set up tracking branches using <br>
 `git branch --set-upstream-to=origin/<branch>` so that git pull automatically fetches and merges the right branch. After setting the remote tracking branch, just check the tracking status using `git branch -vv`

## **Ammending Last Commit Messages**
To change the most recent commit message that is still on your local Git repository, you can run the Git command below:

```sh
git commit --amend -m "New commit message"
```
This changes the latest commit message. The -m option lets you write a new commit message without Git opening your default text editor. To see the change, you can run the Git command below:
```sh
git log
```
You can type `:q` to exit.

Furthermore, if the commit you amended is already in a remote repository, then you will need to forcefully push it to the remote. Assuming you are currently on the development branch or a feature branch and __not__ in `main` branch, run the Git command below to do this:
```sh
git push origin feature1 --force
```
From above, the remote repository (i.e. origin) will be updated to reflect the updated commit message.

## **Adding and editing remote origins**

To add a remote origin to your git repo use the follwing command
```sh
git remote add origin <remote-url>
```

To reset the remote url
```sh
git remote set-url origin <new-remote-url>
```

## **Navigating between git commits**

### Move **back** to a previous commit:

You can navigate to any particular commit using it's commit hash (the unique identifier of the commit). This way is called absolute referencing.

```bash
# get the commit hashes of all commmits
git log --oneline --all --graph --decorate
# navigate to a particular commit-hash
git checkout <commit-hash>
```

This puts your working directory into a **detached HEAD** state at that commit.

You can also use relative referencing like `HEAD~1` (1 commit before HEAD), `HEAD~2`, ..., `HEAD~n` etc.


```bash
git checkout HEAD~1
```

---

### Using a Temporary branch:

If you want to test code at a past commit and then come back, you can use a temporary branch:

  ```bash
  # checkout to a commit on a temporary branch
  git checkout -b temp <commit-hash>
  ```
  The above command creates a new temporary branch. The state of the project will be as it was on the commit hash specified.

  After testing the changes on the temporary branch you can navigate back to the latest commit on your main or feature branch you were workig on earlier using the below command:

  ```bash
  git checkout your-original-branch
  ```


---

### Move **forward** (back to latest commit / branch):

If you checked out a previous commit and now want to go back:

```bash
git checkout main
# or the branch you were on, e.g.
git checkout feature-branch
```

You can also use:

```bash
git checkout -
```

The above command switches you back to the **previous branch**.

> [!NOTE]
>
> * The opposite of `~` (child) is `^` (parent). An example would be `git checkout HEAD^2` to move two commits fast forward from the current HEAD pointer. You can try it by yourself.
>
> * For detailed git log along with decorated git graph, use the following git command: `git log --oneline --all --graph --decorate`

