# 👾 Git Intermediate Training

### Accompanying technical documentation for the LinkedIn Learning course Git Intermediate Techniques. I will leave the original README.md notes from the course  below. The origional course can be accessed via LinkedIn Learning.
---

# Intermediate Git Concepts

## 1. `git push`
The `git push` command uploads local repository content to a remote repository. It's commonly used to share commits with others after committing locally.

### Code Examples:

```bash
# Example 1: Pushing changes to the default (origin) remote repository and branch
git push origin main

# Example 2: Pushing a specific branch to the remote
git push origin feature-branch

# Example 3: Force pushing to overwrite remote changes (use cautiously)
git push --force origin main
```
> **Scenario**: After making several commits locally, you use `git push` to send your updates to the main remote repository so others can pull them.

---

## 2. `git remote -v`
The `git remote -v` command shows the URLs of the remote repositories you're connected to. Useful to check where your repository is pushing or pulling from.

### Code Examples:

```bash
# Example 1: List all remote connections
git remote -v

# Example 2: Adding a new remote and verifying it's listed
git remote add upstream https://github.com/other-repo.git
git remote -v

# Example 3: Checking remote URLs after cloning a repository
git clone https://github.com/your-repo.git
cd your-repo
git remote -v
```
> **Scenario**: You want to check whether your repository is connected to the correct remote URLs before pushing changes.

---

## 3. `git push --force`
The `git push --force` command is used to forcefully push changes to a remote repository, potentially overwriting changes on the remote. Be cautious when using this.

### Code Examples:

```bash
# Example 1: Force push changes to the main branch
git push --force origin main

# Example 2: Force push a feature branch after a rebase
git rebase main
git push --force origin feature-branch

# Example 3: Force push with lease (safer version)
git push --force-with-lease origin main
```
> **Scenario**: After rebasing your branch, you need to use `git push --force` to update the remote branch with your new commit history.

---

## 4. `git fetch`
The `git fetch` command downloads changes from a remote repository without merging them into your working directory.

### Code Examples:

```bash
# Example 1: Fetching changes from the default remote (origin)
git fetch origin

# Example 2: Fetching changes from a specific branch
git fetch origin feature-branch

# Example 3: Fetching all remote branches
git fetch --all
```
> **Scenario**: You want to see updates from a remote branch without merging them into your local branch yet.

---

## 5. `git merge`
The `git merge` command integrates changes from one branch into another. Typically, it's used to combine changes from a feature branch into the main branch.

### Code Examples:

```bash
# Example 1: Merging a feature branch into the main branch
git checkout main
git merge feature-branch

# Example 2: Merging changes from a remote-tracking branch
git checkout main
git merge origin/main

# Example 3: Resolving conflicts during a merge
git merge feature-branch
# If conflicts occur, resolve them in the files and then
git add <file>
git commit
```
> **Scenario**: After finishing a feature, you merge it into the main branch to make the new feature part of the production code.

---

## 6. `git rejected`
"Git rejected" errors often occur when your local branch and the remote branch diverge. This happens when your local branch has changes that the remote branch doesn't have.

### Code Examples:

```bash
# Example 1: Common rejected push error
git push origin main
# ! [rejected] main -> main (fetch first)

# Example 2: Fetch and rebase to avoid rejection
git fetch origin
git rebase origin/main

# Example 3: Resolve by pulling the latest changes
git pull origin main
git push origin main
```
> **Scenario**: You try to push changes but encounter a "rejected" error because your local branch is behind the remote branch.

---

## 7. `git origin`
The `origin` in Git refers to the default remote repository when you clone or initialize a repository. It can be renamed or replaced.

### Code Examples:

```bash
# Example 1: Viewing the origin remote
git remote -v

# Example 2: Renaming the origin remote to upstream
git remote rename origin upstream

# Example 3: Adding a new origin
git remote add origin https://github.com/your-repo.git
```
> **Scenario**: You want to confirm or change the remote repository you're interacting with.

---

## 8. `git log`
The `git log` command displays the commit history of the current branch. It’s useful for reviewing changes, authors, and commit messages.

### Code Examples:

```bash
# Example 1: View the basic commit history
git log

# Example 2: Viewing the log with one-line summaries
git log --oneline

# Example 3: Viewing the history for a specific file
git log -- <file-name>
```
> **Scenario**: You're reviewing the history of commits to track down when a bug was introduced.

---

## 9. `git fetch remote changes`
Fetching remote changes allows you to retrieve updates from a remote repository without integrating them.

### Code Examples:

```bash
# Example 1: Fetch all branches from the remote
git fetch origin

# Example 2: Fetch changes for a specific branch
git fetch origin feature-branch

# Example 3: Fetch and list branches updated remotely
git fetch --all
```
> **Scenario**: You want to see if anyone has pushed changes to the remote before updating your local branches.

---

## 10. Seeing what's merged to Git branch
You can check what commits have been merged into your current branch using `git log`.

### Code Examples:

```bash
# Example 1: Check for merged commits
git log --merges

# Example 2: Check if a specific branch has been merged
git branch --merged

# Example 3: Check what’s merged in relation to another branch
git log main..feature-branch --merges
```
> **Scenario**: Before deleting a branch, you check whether it has been fully merged into the main branch.

---

## 11. Creating branches
Creating branches allows you to work on features independently from the main codebase.

### Code Examples:

```bash
# Example 1: Create a new feature branch
git checkout -b feature-branch

# Example 2: Switch to an existing branch
git checkout main

# Example 3: List all branches
git branch
```
> **Scenario**: You create a new branch to work on a feature without affecting the main branch.

---

## 12. Git merge best practices
Merge best practices involve keeping your branches up to date and resolving conflicts properly.

### Code Examples:

```bash
# Example 1: Keep feature branches up-to-date before merging
git fetch origin
git merge origin/main

# Example 2: Squashing commits before merging to clean up history
git merge --squash feature-branch

# Example 3: Merge using a pull request workflow
# Use PRs to review changes before merging.
```
> **Scenario**: Ensuring smooth merges by updating branches frequently and squashing commits for cleaner history.

---

## 13. `git merged` and `git no-merged`
Check which branches have been merged or not merged.

### Code Examples:

```bash
# Example 1: List branches that have been merged into the current branch
git branch --merged

# Example 2: List branches that have NOT been merged
git branch --no-merged

# Example 3: Check merged state between specific branches
git log --merges main..feature-branch
```
> **Scenario**: You verify if a branch can be safely deleted after confirming it has been merged.

---

## 14. `git prune`
The `git prune` command removes orphaned or unreachable objects in your repository. It’s commonly used to clean up deleted branches.

### Code Examples:

```bash
# Example 1: Remove orphaned objects after deleting branches
git prune

# Example 2: Prune remote-tracking branches that no longer exist
git fetch --prune

# Example 3: Dry run to see what would be pruned
git prune --dry-run
```
> **Scenario**: After deleting branches, you use `git prune` to clean up any remaining loose objects.

---

## 15. `git dry run`
The `git dry run` option allows you to simulate the outcome of a command without actually executing it.

### Code Examples:

```bash
# Example 1: Simulate a push command
git push --dry-run origin main

# Example 2: Simulate pruning objects
git prune --dry-run

# Example 3: Simulate deleting a branch
git branch -d feature-branch --dry-run
```
> **Scenario**: Before executing a potentially risky command, you run it with `--dry-run` to preview the outcome.

---
Author: Kodebae
---



## Git Intermediate Techniques
This is the repository for the LinkedIn Learning course Git Intermediate Techniques. The full course is available from [LinkedIn Learning][lil-course-url].

![Git Intermediate Techniques][lil-thumbnail-url] 

Enhance your Git skillset, and explore intermediate techniques and concepts that can help you work more efficiently with the popular open-source version control software. Instructor Kevin Skoglund shares branch management techniques, like deleting and pruning, and how to use tags to mark important points in the branch history. Learn to use interactive staging to stage small portions of a file, cherry-picking to share commits between branches, patches to share commits with others, and techniques for tracking down problems in your project. Kevin demystifies the rebase command and explains when to choose rebasing over merging.

## Instructions
- You can follow along using the GutHub repository.
- You can also download the whole repository by cloning it. 
- You don't need to have a GitHub account to follow along. You can click the code button on the main repo page and then choose the download option for downloading a zip file that contains the repository. 

The repository includes directories for each chapter and video in the course. You can navigate to the directory that corresponds to the video that you're watching. The files for the start of the course are in chapter 01 and the first file is 0101.zip. Each zip file contains a separate git repository containing the files and commits as they exist at the start of the video. Each repository has been compressed so they can exist inside the main GitHub repository. You can also just download a single set of exercise files by clicking on the name and then on the download button.

### Instructor

Kevin Skoglund 
                            


                            

Check out my other courses on [LinkedIn Learning](https://www.linkedin.com/learning/instructors/kevin-skoglund).

[lil-course-url]: https://www.linkedin.com/learning/git-intermediate-techniques-16077011?dApp=59033956
[lil-thumbnail-url]: https://cdn.lynda.com/course/3082618/3082618-1668022974716-16x9.jpg
