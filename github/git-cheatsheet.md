# Git Cheatsheet

## Starting a project

- Open terminal
- Navigate to project folder
- RUN: `git init`
   - this creates `.git` folder that initializes the folder as a git repository
- *Create project files*
- RUN: `git status`
   - Should list of all files that you created (and are not gitignored)
   - These files should be "untracked"/ "not committed"
- RUN: `git add .`
   - This command adds all files shown under `git status`
   -  to specify files to add, RUN: `git add filename`, replacing `filename` with the file you wish to add
- RUN: `git commit -m "Inits project"`
   -  This saves all files added from `git add` into the git repository and attaches the message `Inits project` to the commit
   -  Replace the message with your own message
- RUN: `git branch -M main`
   - change default branch name "master" to main
   - optional
- Login into github.com
- Create new repository
- Get Repository clone link (see [guide](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)) 
- Back in terminal, RUN: `git remote add origin gitCloneLink`
- RUN: `git push -u origin main`
   - This pushes your repository to the repository created online
   - Replace `main` with the name of the branch you are pushing

## Common Git Commands

*A Quick reference for commonly used git commands*

**NOTE**: `<>` are placeholders; do not include them in the git commnads you execute

## Working on new code

