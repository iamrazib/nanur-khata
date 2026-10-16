## Nanu's Khata — My Git Learning Journey

## Chapter 1: The First Recipe

Nanu asked me to preserve her traditional bhapa pitha recipe before winter. I started by configuring my Git username and email using git config --global. Then I created a folder named nanur-khata and initialized a Git repository using git init.

Next, I created bhapa-pitha.md and checked its status using git status. Initially, Git showed the file as untracked. I used git add bhapa-pitha.md to move it into the staging area.

Nanu then corrected the gur measurement from 2 cups to 1.5 cups. I edited the file and ran git diff to inspect the unstaged change. After staging the correction, I ran git diff --staged to review the content prepared for the commit.

I saved the recipe using a meaningful git commit -m message. Finally, I accidentally staged bazar-list.txt and used git reset bazar-list.txt to unstage it without deleting the file.

## Commands Used

git config --global user.name "Sk. Razibul Islam"
git config --global user.email "iamrazib@gmail.com"
git init
git branch -M main
git status
git add bhapa-pitha.md
git diff
git diff --staged
git commit -m "Add Nanu's bhapa pitha recipe with corrected gur measurement"
git add bazar-list.txt
git reset bazar-list.txt
git log --oneline

## What I Learned

I learned how to initialize a repository, track files, compare staged and unstaged changes, and create meaningful commits. I also learned that unstaging a file does not delete it from my computer.

## Screenshot Evidence

Screenshot 1: Git initialization.
Screenshot 2: Recipe staging.
Screenshot 3: unstaged measurement correction.
Screenshot 4: staged diff output.
Screenshot 5: First commit.
Screenshot 6: Unstaging the shopping list.


## Chapter 2: The Secret Spice

Nanu warned me that her secret spice recipe must never be uploaded to GitHub. To protect it, I created a file named `secret-masala.txt`, two temporary files ending in `.tmp`, and a `draft` folder containing an unfinished recipe.

I created a `.gitignore` file and added three rules: `secret-masala.txt`, `*.tmp`, and `draft/`. These rules tell Git to ignore the confidential recipe, temporary files, and unfinished drafts.

After saving `.gitignore`, I ran `git status` and noticed that the ignored files were no longer listed as untracked. I also executed `git check-ignore -v` to verify which rules were responsible for ignoring each file.

Finally, I committed `.gitignore` with the message "Protect secret spice recipe and exclude temporary drafts".

### Commands Used

New-Item secret-masala.txt -ItemType File
New-Item cooking-notes.tmp -ItemType File
New-Item recipe-backup.tmp -ItemType File
New-Item draft -ItemType Directory
New-Item draft\unfinished-recipe.md -ItemType File
git status
git check-ignore -v secret-masala.txt cooking-notes.tmp recipe-backup.tmp draft/unfinished-recipe.md
git ls-files -- secret-masala.txt
git add .gitignore
git commit -m "Protect secret spice recipe and exclude temporary drafts"


### What I Learned

I learned that `.gitignore` prevents untracked confidential and unnecessary files from being included in future commits. I also learned how to verify ignore rules using `git check-ignore` and how to confirm that a secret file is not tracked using `git ls-files`.

This is important in DevOps because developers must prevent sensitive data and temporary files from entering shared repositories.

### Screenshot Evidence

Screenshot 7: Git status before creating `.gitignore`.
Screenshot 8: Ignore rules and verification results.
Screenshot 9: Successful `.gitignore` commit.


## Chapter 3: The Eid Special

Nanu wanted me to prepare biryani and shemai recipes for Eid without changing the main recipe book immediately. I created a new Git branch named `eid-special` using `git branch eid-special` and switched to it using `git checkout eid-special`.

On this branch, I created `biryani.md` and `shemai.md`. I saved each recipe in a separate commit with a meaningful commit message. This helped me understand how branches allow developers to work on new features independently.

Next, I switched back to `main` and checked whether the Eid recipes were available. The files were not present because the changes belonged to the `eid-special` branch. After running `git merge eid-special`, both recipes became available on the main branch.

### Merge Conflict Challenge

To understand merge conflicts, I created another branch named `conflict-demo`. I changed the cardamom measurement to 4 pods on `main` and 6 pods on `conflict-demo`.

When I attempted to merge the branches, Git reported a conflict in `biryani.md`. I opened the file, examined the conflicting changes, and selected 4 cardamom pods as the final measurement.

I removed the conflict markers, staged the corrected file, and committed the resolution.

### Commands Used

git branch eid-special
git checkout eid-special
git add biryani.md
git commit -m "Add Nanu's Eid biryani recipe"
git add shemai.md
git commit -m "Add Nanu's traditional Eid shemai recipe"
git checkout main
git merge eid-special
git log --oneline --graph --all
git branch conflict-demo
git add biryani.md
git commit -m "Adjust biryani cardamom measurement on main"
git checkout conflict-demo
git add biryani.md
git commit -m "Propose alternative cardamom measurement"
git checkout main
git merge conflict-demo
git add biryani.md
git commit -m "Resolve biryani cardamom measurement merge conflict"


### What I Learned

I learned that Git branches allow developers to work independently without affecting the main project. I also learned how to merge changes and resolve conflicts when two branches modify the same content.

A merge conflict does not mean Git is broken. It means Git needs a developer to review the competing changes and decide the final content.

### Screenshot Evidence

**Screenshot 1:** Creating and switching to `eid-special`.
**Screenshot 2:** Separate biryani and shemai commits.
**Screenshot 3:** Eid recipes absent from the main branch.
**Screenshot 4:** Successful merge of `eid-special`.
**Screenshot 5:** Intentional merge conflict in `biryani.md`.
**Screenshot 6:** Conflict resolution and commit history.

