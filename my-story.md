## Nanu's Khata — My Git Learning Journey

## Chapter 1: The First Recipe

Nanu asked me to preserve her traditional bhapa pitha recipe before winter. I started by configuring my Git username and email using git config --global. Then I created a folder named nanur-khata and initialized a Git repository using git init.

Next, I created bhapa-pitha.md and checked its status using git status. Initially, Git showed the file as untracked. I used git add bhapa-pitha.md to move it into the staging area.

Nanu then corrected the gur measurement from 2 cups to 1.5 cups. I edited the file and ran git diff to inspect the unstaged change. After staging the correction, I ran git diff --staged to review the content prepared for the commit.

I saved the recipe using a meaningful git commit -m message. Finally, I accidentally staged bazar-list.txt and used git reset bazar-list.txt to unstage it without deleting the file.

## Commands Used
```text
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
```

## What I Learned

I learned how to initialize a repository, track files, compare staged and unstaged changes, and create meaningful commits. I also learned that unstaging a file does not delete it from my computer.

## Screenshot Evidence

**Screenshot 1:** Git initialization.
**Screenshot 2:** Recipe staging.
**Screenshot 3:** unstaged measurement correction.
**Screenshot 4:** staged diff output.
**Screenshot 5:** First commit.
**Screenshot 6:** Unstaging the shopping list.


## Chapter 2: The Secret Spice

Nanu warned me that her secret spice recipe must never be uploaded to GitHub. To protect it, I created a file named `secret-masala.txt`, two temporary files ending in `.tmp`, and a `draft` folder containing an unfinished recipe.

I created a `.gitignore` file and added three rules: `secret-masala.txt`, `*.tmp`, and `draft/`. These rules tell Git to ignore the confidential recipe, temporary files, and unfinished drafts.

After saving `.gitignore`, I ran `git status` and noticed that the ignored files were no longer listed as untracked. I also executed `git check-ignore -v` to verify which rules were responsible for ignoring each file.

Finally, I committed `.gitignore` with the message "Protect secret spice recipe and exclude temporary drafts".

### Commands Used
```text
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
```

### What I Learned

I learned that `.gitignore` prevents untracked confidential and unnecessary files from being included in future commits. I also learned how to verify ignore rules using `git check-ignore` and how to confirm that a secret file is not tracked using `git ls-files`.

This is important in DevOps because developers must prevent sensitive data and temporary files from entering shared repositories.

### Screenshot Evidence

**Screenshot 7:** Git status before creating `.gitignore`.
**Screenshot 8:** Ignore rules and verification results.
**Screenshot 9:** Successful `.gitignore` commit.
**Screenshot 10:** Final commit.
**Screenshot 11:** Final verification.


## Chapter 3: The Eid Special

Nanu wanted me to prepare biryani and shemai recipes for Eid without changing the main recipe book immediately. I created a new Git branch named `eid-special` using `git branch eid-special` and switched to it using `git checkout eid-special`.

On this branch, I created `biryani.md` and `shemai.md`. I saved each recipe in a separate commit with a meaningful commit message. This helped me understand how branches allow developers to work on new features independently.

Next, I switched back to `main` and checked whether the Eid recipes were available. The files were not present because the changes belonged to the `eid-special` branch. After running `git merge eid-special`, both recipes became available on the main branch.

### Merge Conflict Challenge

To understand merge conflicts, I created another branch named `conflict-demo`. I changed the cardamom measurement to 4 pods on `main` and 6 pods on `conflict-demo`.

When I attempted to merge the branches, Git reported a conflict in `biryani.md`. I opened the file, examined the conflicting changes, and selected 4 cardamom pods as the final measurement.

I removed the conflict markers, staged the corrected file, and committed the resolution.

### Commands Used
```text
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
```

### What I Learned

I learned that Git branches allow developers to work independently without affecting the main project. I also learned how to merge changes and resolve conflicts when two branches modify the same content.

A merge conflict does not mean Git is broken. It means Git needs a developer to review the competing changes and decide the final content.

### Screenshot Evidence

**Screenshot 12:** Creating and switching to `eid-special`.
**Screenshot 13:** Separate biryani and shemai commits.
**Screenshot 14:** Eid recipes absent from the main branch.
**Screenshot 15:** Successful merge of `eid-special`.
**Screenshot 16:** Intentional merge conflict in `biryani.md`.
**Screenshot 17:** Conflict resolution and commit history.



## Chapter 4: Mitu Joins In

Nanu's recipe book was growing, and my cousin Mitu in Chattogram wanted to contribute. I created a GitHub repository named `nanur-khata` and connected it to my local project using `git remote add origin`. I then uploaded my existing recipes using `git push -u origin main`.

To simulate Mitu working remotely, I cloned the repository into a separate folder using `git clone`. I configured a local Git author identity for Mitu and created a new recipe named `chittagong-mezban.md`. After adding and committing the recipe, I pushed the change to GitHub.

Back in my original project, I ran `git fetch origin` to download Mitu's new commit. I checked the remote changes and confirmed that the Mezban recipe was not yet present locally. After executing `git merge origin/main`, the recipe appeared in my original project.

Later, Mitu added serving suggestions and pushed another commit. This time, I used `git pull` to download and integrate the updated recipe in one step.

### Commands Used

```text
git remote add origin https://github.com/iamrazib/nanur-khata.git
git push -u origin main
git clone https://github.com/iamrazib/nanur-khata.git mitu-nanur-khata
git config user.name "Mitu"
git config user.email "mitu@example.com"
git add chittagong-mezban.md
git commit -m "Mitu adds traditional Chattogram Mezban recipe"
git push origin main
git fetch origin
git log --oneline main..origin/main
git merge origin/main
git add chittagong-mezban.md
git commit -m "Mitu adds serving suggestions to Mezban recipe"
git push origin main
git pull --no-rebase origin main
```

### Difference Between Fetch + Merge and Pull

I learned that `git fetch` downloads new commits from GitHub without modifying the current branch. After reviewing the changes, I can use `git merge origin/main` to integrate them.

In contrast, `git pull` combines fetching and integration in a single command. It is faster for routine updates, while separate fetching and merging allows more control over reviewing changes before integration.

### What I Learned

This chapter taught me how multiple contributors can work on the same GitHub repository from different locations. I learned how to clone a repository, contribute changes, push commits, fetch updates, merge remote changes and keep local files synchronized.

It also demonstrated why clear commit messages and regular synchronization are important when several developers work on one project.

### Screenshot Evidence

**Screenshot 18:** Connecting the local repository and pushing to GitHub.
**Screenshot 19:** Mitu cloning the repository and pushing the Mezban recipe.
**Screenshot 20:** Fetching and merging Mitu's changes.
**Screenshot 21:** Mitu's second update and successful git pull.



### Chapter 5: Half-Cooked Halua and Time Travel

Nanu asked me to prepare suji halua, so I created `halua.md` and committed the initial recipe. While updating the cooking instructions, Nanu reminded me that the biryani needed an additional cardamom instruction.

I used `git stash` to save my unfinished halua changes temporarily. Then I updated `biryani.md` and committed the correction. Afterward, I ran `git stash pop` to restore the halua changes and complete the recipe.

Next, I organized the family recipes into `recipes/eid/` and `recipes/traditional/` using `git mv`. I also created an outdated recipe and removed it using `git rm` to understand how Git tracks deletions. I examined the commit history using `git log --stat -M`.

To inspect a previous change, I selected a commit SHA from `git log --oneline` and ran `git show` to view its details.

Finally, I created a separate branch named `time-travel-test` and committed a temporary file. I used `git reset --hard HEAD~1` to return to the previous commit. The temporary file disappeared, showing how a hard reset can remove changes introduced by a later commit from the current branch's working version.

### Commands Used

```text
git stash push -m "Unfinished halua cooking instructions"
git stash list
git add biryani.md
git commit -m "Improve biryani recipe with cardamom preparation instruction"
git stash pop
git mv bhapa-pitha.md recipes/traditional/
git mv halua.md recipes/traditional/
git mv biryani.md recipes/eid/
git mv shemai.md recipes/eid/
git mv chittagong-mezban.md recipes/traditional/
git rm old-recipe.md
git log --stat -M
git log --oneline
git show MY_COMMIT_SHA
git checkout -b time-travel-test
git reset --hard HEAD~1
```

### Why Are Rebase and Reset --Hard Dangerous on Shared Branches?

I learned that `git rebase` rewrites commit history, which may create synchronization problems for other collaborators. I also learned that `git reset --hard` can discard uncommitted tracked changes and move a branch back to an earlier commit.

Using these commands carelessly on shared branches can disrupt teamwork or lead to lost work. Therefore, I practiced the reset command only on a separate testing branch.

### What I Learned

This chapter taught me how to temporarily save unfinished work, switch between urgent tasks, organize tracked files, inspect historical commits, and experiment with earlier versions of a project.

The most important lesson was to protect committed work and use potentially destructive Git commands carefully.

### Screenshot Evidence

**Screenshot 22:** Using git stash.
**Screenshot 23:** Restoring changes using git stash pop.
**Screenshot 24:** Moving and deleting recipes with git mv and git rm.
**Screenshot 25:** Inspecting a previous commit with git show.
**Screenshot 26:** Reset experiment on time-travel-test branch.
