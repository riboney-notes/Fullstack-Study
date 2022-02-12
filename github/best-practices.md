# Git commit message practices (Sources used: [freecodecamp](https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/))

* Command to configure default editor for git commit messages: 
    `git config --global core.editor <your-text-editor-choice>`

* Commit message format (if doing `git commit` only):
```
Subject (short description). About 50 characters. Leave blank line after this

Here is the extended description (body) of the commit message. 
Should be about 72 characters. 
Contains detailed explanatory description of the change/ commit
```

* Commit message format (if doing `git commit -m`)
`git commit -m "Subject here" -m "Further description here..."`

* Some guidelines on good commit message practices:

```
1. Specify the type of commit (ex: feat, fix, style, refactor, etc.)
2. Separate the subject from the body with blank line
3. Capitalize the subject line and each paragrah
4. Use imparative mood in the subject line
   4a. Imperative mood = written as if giving a command or instruction
   4b. Ex: "Update database schemas" "Refactor User class for readability"

```
