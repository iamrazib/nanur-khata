Nanu's Khata — My Git Learning Journey

Chapter 1: The First Recipe

Nanu asked me to preserve her traditional bhapa pitha recipe before winter. I started by configuring my Git username and email using git config --global. Then I created a folder named nanur-khata and initialized a Git repository using git init.

Next, I created bhapa-pitha.md and checked its status using git status. Initially, Git showed the file as untracked. I used git add bhapa-pitha.md to move it into the staging area.

Nanu then corrected the gur measurement from 2 cups to 1.5 cups. I edited the file and ran git diff to inspect the unstaged change. After staging the correction, I ran git diff --staged to review the content prepared for the commit.

I saved the recipe using a meaningful git commit -m message. Finally, I accidentally staged bazar-list.txt and used git reset bazar-list.txt to unstage it without deleting the file.

Commands Used

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

What I Learned

I learned how to initialize a repository, track files, compare staged and unstaged changes, and create meaningful commits. I also learned that unstaging a file does not delete it from my computer.

Screenshot Evidence

Insert Screenshot 1: Git initialization.
Insert Screenshot 2: Recipe staging.
Insert Screenshot 3: unstaged measurement correction.
Insert Screenshot 4: staged diff output.
Insert Screenshot 5: First commit.
Insert Screenshot 6: Unstaging the shopping list.

