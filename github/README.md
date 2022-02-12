# Git & Github Setup

## Requirements
- Windows
- Linux
- MacOs
- Terminal
  - *On Windows, this is powershell or command prompt or git bash*

## Install
1. Open terminal
2. Check if you have git already installed, by typing and entering: `git version`
    - If it shows you the version number, then git is already installed
    - If it shows that `git` is an unknown command, then git is not installed, and need to be installed
      - [Windows Installation](https://gitforwindows.org/)
      - [Mac Installation](https://git-scm.com/download/mac)
      - Debian/Ubuntu - Run: `sudo apt-get install git-all`
      - RPM - Run: `sudo dnf install git-all`

## Basic Setup
1. Open terminal
2. Check if `username` and `email` is already configured by entering: `git config --list` 
   - If it is empty, then *proceed with step 3*
   - If it is present, then *skip section*
3. Setup git with name and email (your commits will be signed with the name and email you set here)
   - Run: `git config --global user.name "Insert your name here"`
   - Run: `git config --global user.email insertEmailHere@example.com`
4. Run: `git config --list`
   - *to verify changes have taken effect *


## References
- [Installing Git](https://github.com/git-guides/install-git)
- [Your first time with git and github](https://kbroman.org/github_tutorial/pages/first_time.html)
- [Git setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
  



