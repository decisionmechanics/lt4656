<img src="images/learning-tree-logo.svg" alt="Learning Tree logo" width="300" style="margin-bottom: 1rem;" />

# Introduction to Git exercises

## Exercise 0: Bash basics

Execute the following commands in the terminal (Linux/macOS) or Git Bash (Windows).

Navigate to your home folder (e.g. `/home/student`).

```bash
cd
```

The current folder you are in is shown in your prompt.

If you are following using your own installation of Git Bash on Windows, you can navigate to the root of the `C:` drive as follows.

```bash
cd /c
```

Navigate to the `course` subfolder.

```bash
cd course
```

Change to the `course` folder using its full path (relative to the root of your home folder).

```bash
cd ~/course
```

If you are following using your own installation of Git Bash on Windows, you can change to the `course` folder using its full path (relative to the root of the `C:` drive) as follows.

```bash
cd /c/course
```

Note that the current folder can be referred to with `.` (single period) and the parent folder is `..` (double period).

List the files/folders in the current folder.

```bash
ls
```

List the files in the current folder, _including hidden (dot) files/folders_.

```bash
ls -a
```

Create a subfolder.

```bash
mkdir my-project
```

Navigate to the `my-project` subfolder.

```bash
cd my-project
```

Create an empty file.

```bash
touch README.txt
```

List the files in the folder.

```bash
ls
```

Edit the file.

```bash
code README.txt
```

Save the file and close the editor.

Review the contents of `README.txt`.

```bash
cat README.txt
```

Delete `README.txt`.

```bash
rm README.txt
```

Confirm the file has gone.

```bash
ls
```

Navigate to the parent folder (i.e. `my-project`).

```bash
cd ..
```

Delete the `my-project` folder.

```bash
rmdir my-project
```

Confirm that the `my-project` folder has been deleted.

```bash
ls
```

Note that you may delete a folder and all its contents using `rm -rf <folder-path>`. Be _very, very_ careful if you use this command as you can lose a lot of data and even corrupted your operating system if you use it in the wrong place.

## Exercise 1: Configuring Git

Set your name and e-mail address. These are used by Git to track who committed changes to the repository.

```bash
git config --global user.name "Chris Doe"
git config --global user.email "chrisdoe@example.com"
```

Obviously, use your own details here.

The following global settings have already been configured in your virtual machine. If you are using your own computer, the settings may be different.

```bash
git config --global core.editor "code --wait"
git config --global --replace-all core.pager "less -F -X"
```

Review the configuratipon settings.

```bash
git config --list --global
```

## Exercise 2: Initializing a new Git repository.

This exercise assumes Git is configured (e.g. as performed in Exercise 1).

Ensure you are in the home/root folder before you start (e.g. `cd ~/`).

Make a new project folder and navigate to it.

```bash
mkdir planets-project
cd planets-project
```

Check that it's not already a Git repository.

```bash
git status
```

Intialize as a new Git repository.

```bash
git init
```

Check that the repository now exists.

```bash
git status
```

List the (hidden) files and folders.

```bash
ls -a
```

A `.git` folder has been created. This is the Git repository.

## Exercise 3: Committing files

This exercise follows from Exercise 2.

Check the status of your repository.

```bash
git status
```

Create a new `planets.txt` file.

```bash
touch planets.txt
```

Check the status of your repository.

```bash
git status
```

Stage `planets.txt`.

```bash
git add planets.txt
```

Check the status of your repository.

```bash
git status
```

Commit the staged changes.

```bash
git commit -m "Create planets file"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

## Exercise 4: Committing modifications

This exercise follows from Exercise 3.

Check the status of your repository.

```bash
git status
```

Edit `planets.txt`.

```bash
code planets.txt
```

Add a line with the text `Mercury`. Save the file and quit the editor.

Check that `planets.txt` has been changed.

```bash
git status
```

Stage the changes.

```bash
git add planets.txt
```

Check the status of your repository.

```bash
git status
```

Commit the staged changes.

```bash
git commit -m "Add Mercury"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

## Exercise 5: Branching

This exercise follows from Exercise 4.

Check the status of your repository.

```bash
git status
```

Create a new `stars` branch and switch to it.

```bash
git switch -c stars
```

Review the branches.

```bash
git branch
```

Create a new `stars.txt` file.

```bash
touch stars.txt
```

Check the status of your repository.

```bash
git status
```

Stage `stars.txt`

```bash
git add stars.txt
```

Check the status of your repository.

```bash
git status
```

Commit the staged changes.

```bash
git commit -m "Create stars file"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

Switch back to the `master` branch.

```bash
git switch master
```

Examine your commit log.

```bash
git log --oneline
```

The `Create stars file` commit isn't there.

List the files.

```bash
ls
```

The `stars.txt` file isn't there---it's on the `stars` branch.

## Exercise 6: Fast-forward merging

This exercise follows from Exercise 5.

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

Merge the `stars` branch into the `master` (current) branch.

```bash
git merge stars
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

The `master` branch is now pointing to the `Create stars file` commit.

List the files.

```bash
ls
```

The `stars.txt` file is now present on the master branch.

## Exercise 7: Merging with conflicts

This exercise follows from Exercise 6.

Check the status of your repository.

```bash
git status
```

Edit `stars.txt` file. Add the text `Sun` as the only line.

Stage and commit the changes.

```bash
git commit -am "Add the Sun"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

Switch to the `stars` branch.

```bash
git switch stars
```

Edit `stars.txt` file. Note that it's empty. We made the previous changes on a different branch. Add the text `Proxima Centauri` as the only line.

Stage and commit the changes.

```bash
git commit -am "Add Proxima Centauri"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

Merge the `master` branch into the current (`stars`) branch.

```bash
git merge master
```

Read the message. There's a conflict in `stars.txt`---we have two different stars.

Check the status of your repository.

```bash
git status
```

Resolve the conflict by following the instructions in the message.

Edit `stars.txt`. See that Git has added conflict markers. Resolve the conflict by accepting both additions. Save the file and quit the editor.

Stage and commit the merged changes.

```bash
git commit -am "Merge stars"
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log
```

The most recent commit should be the merge commit.

You can review the visual representation of the branches being merged.

```bash
git log --oneline --graph
```

Merge the `stars` branch into the `master` branch.

```bash
git switch master
git merge stars
```

Check the status of your repository.

```bash
git status
```

Examine your commit log.

```bash
git log --oneline
```

Git was able to perform a fast-forward merge as we'd already merged `master` into `stars`.

Delete the `stars` branch.

```bash
git branch -d stars
```

Confirm the `stars` branch is gone.

```bash
git branch
```

## Exercise 8: Use GitKraken

This exercise follows from Exercise 7.

Open the `planets-project` folder in GitKraken.

Review the commit history.

Make sure you are on the `master` branch.

Edit `planets.txt` to add `Venus` on the next line.

Stage and commit the changes. Use "Add Venus" as the commit message.

Using the terminal, look at the status of the repository and review the commit log.

## Exercise 9: Rebasing onto a branch

This exercise follows from Exercise 8.

Check the status of your repository.

```bash
git status
```

Ensure you are on the `master` branch.

Review the commit log.

```bash
git log --oneline
```

Add a `comets.txt` file.

```bash
touch comets.txt
```

Stage and commit `comets.txt`.

```bash
git add comets.txt
git commit -m "Create comets file"
```

Check the status of your repository.

```bash
git status
```

Create a new `short-period-comets` branch and switch to it.

```bash
git switch -c short-period-comets
```

Edit `comets.txt` and add the text `Halley's Comet`.

Stage and commit the changes.

```bash
git commit -am "Add Halley's Comet"
```

Check the status of your repository.

```bash
git status
```

Switch to the `master` branch.

```bash
git switch master
```

Edit `comets.txt` and add the text `Hale-Bopp`.

Stage and commit the changes.

```bash
git commit -am "Add Hale-Bopp"
```

Check the status of your repository.

```bash
git status
```

Do a rebase merge of branch `short-period-comets` onto `master`.

```bash
git switch short-period-comets
git rebase master
```

There will be a merge conflict. Resolve it following the instructions in the message.

Edit `comets.txt`. See that Git has added conflict markers. Resolve the conflict by accepting both additions. Save the file and quit the editor.

Stage and commit the merged changes.

```bash
git rebase --continue
```

Check the status of your repository.

```bash
git status
```

Review the commit log.

```bash
git log --oneline --graph
```

The commit history is linear---there are no merge commits.

## Exercise 10: Cloning a remote repository

Navigate to the /home/root folder (e.g. `cd`).

Clone the course repository.

```bash
git clone https://github.com/decisionmechanics/lt4656.git
```

Navigate to the newly cloned course folder.

```bash
cd lt4656
```

Review the commit log.

```bash
git log --oneline
```

Confirm where the repository was cloned from.

```bash
git remote -v
```

Get any updates (there won't be any, obviously).

```bash
git pull
```

## Exercise 11: Undoing changes

This exercise follows from Exercise 9.

Navigate to the planets project folder (e.g. `cd ~/planets-project`).

Check the status of your repository.

```bash
git status
```

Make sure you are on the `master` branch.

```bash
git switch master
```

Review the commit log.

```bash
git log --oneline
```

Edit `planets.txt` and add "Pluto" to the end of the file. Save the file and quit the editor.

Check the status of your repository.

```bash
git status
```

Oops. We just released that Pluto is no longer a planet. We could edit the file to remove it. But, what if we had a _lot_ of changes to the file and wanted to go back to our last committed version?

Undo latest changes to `planets.txt`.

```bash
git restore planets.txt
```

Check the status of your repository.

```bash
git status
```

Look at the contents of `planets.txt`.

```bash
cat planets.txt
```

Pluto has gone.

## Exercise 12: Tagging

This exercise follows from Exercise 11.

Check the status of your repository.

```bash
git status
```

List the current tags.

```bash
git tag
```

There shouldn't be any.

Tag the commit that is three commits behind the tip of the `master` branch.

```bash
git tag v1.0.0 HEAD~3
```

Review the commit log. You should see the tag against the earlier commit.

List the tags.

```bash
git tag
```

You should see the `v1.0.0` tag.

## Exercise 13: Disaster recovery using reflogs

This exercise follows from Exercise 11.

Check the status of your repository.

```bash
git status
```

Review the commit log.

```bash
git log --oneline
```

Delete all the commits after the `v1.0.0` commit.

```bash
git reset --hard v1.0.0
```

Review the new commit log.

```bash
git log --oneline
```

We changed our minds! We want those changes back! Oops... That was a bit of a scorched earth operation.

But, all is not lost. We can turn to the reflog.

List the entries in the reflog (restrict it to the last 10 entries).

```bash
git reflog -n 10
```

The latest entry should be the one for the `reset` operation we now regret.

The commit prior to that is `HEAD@{1}`. We'd like to be back there.

Undo the previous `reset` operation.

Review the restored commit log.

```bash
git log --oneline
```
