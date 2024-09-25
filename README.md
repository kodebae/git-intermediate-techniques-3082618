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

# Example 4: Identify remote branches that were merged into the current branch
git branch -r --merged 
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

# Example 4: Prune a remote branch deleted by a team member
git remote prune origin
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

## 16. `git gc`
The `git gc` (garbage collection) command is used to clean up unnecessary files and optimize the local repository.

### Code Examples:

```bash
# Example 1: Run the default garbage collection
git gc

# Example 2: Aggressively clean up files and optimize the repository
git gc --aggressive

# Example 3: Simulate garbage collection to preview changes
git gc --dry-run
```
> **Scenario**: After deleting branches or performing many rebase operations, you run `git gc` to clean up unnecessary objects and optimize performance.

---

## 17. Creating tags with `git`
Tags are used to mark specific points in history, often used for releases or versioning.

### Code Examples:

```bash
# Example 1: Creating a lightweight tag for version 1.0
git tag v1.0

# Example 2: Tagging a specific commit
git tag v1.0 <commit-sha>

# Example 3: Listing all tags in the repository
git tag
```
> **Scenario**: You’re ready to release version 1.0 of your project, and you create a tag to mark the commit.

---

## 18. Creating annotated tags with `-am`
Annotated tags contain additional metadata like the tagger’s name, email, and date, along with a message. They are used when more detailed version tracking is required.

### Code Examples:

```bash
# Example 1: Creating an annotated tag with a message
git tag -a v1.0 -m "Release version 1.0"

# Example 2: Creating an annotated tag for a specific commit
git tag -a v1.1 -m "Hotfix for issue #42" <commit-sha>

# Example 3: Verifying the details of an annotated tag
git show v1.0
```
> **Scenario**: You’re preparing a formal release and want to add extra details about what’s included in the release via an annotated tag.

---

## 19. Deleting tags
Tags can be deleted locally and remotely when no longer needed.

### Code Examples:

```bash
# Example 1: Deleting a local tag
git tag -d v1.0

# Example 2: Deleting a remote tag
git push origin --delete v1.0

# Example 3: Delete multiple local tags at once
git tag -d v1.0 v1.1 v1.2
```
> **Scenario**: You made a mistake with a tag name or need to remove an old version tag from both the local and remote repositories.

---

## 20. `git switch`
`git switch` is an alternative to `git checkout` for switching branches, with a clearer syntax for branch switching.

### Code Examples:

```bash
# Example 1: Switch to an existing branch
git switch main

# Example 2: Create and switch to a new branch
git switch -c feature-branch

# Example 3: Switch to a remote-tracking branch
git switch origin/feature-branch
```
> **Scenario**: You're working on multiple branches and want to quickly switch between them using a simpler syntax.

---

## 21. `git SHA`
The SHA (Secure Hash Algorithm) in Git is a unique identifier for every commit. It helps track specific commits and allows for precise referencing.

### Code Examples:

```bash
# Example 1: Viewing the SHA for recent commits
git log --oneline

# Example 2: Checkout a commit using its SHA
git checkout <commit-sha>

# Example 3: Referencing a commit SHA in a tag
git tag v2.0 <commit-sha>
```
> **Scenario**: You need to revert your working directory to a specific commit identified by its SHA.

---

## 22. `git --tags`
The `git --tags` option is used with commands to include tags in their output.

### Code Examples:

```bash
# Example 1: Fetch tags from the remote repository
git fetch --tags

# Example 2: List all commits including tags
git log --tags

# Example 3: Push tags to the remote repository
git push --tags
```
> **Scenario**: You want to ensure that tags are included when fetching changes or listing commit history.

---

## 23. Why and when to create tags
Tags are useful for marking significant points in a repository's history, like release versions or milestones.

### Code Examples:

```bash
# Example 1: Tagging a release version
git tag v1.0

# Example 2: Creating a tag for a milestone in development
git tag milestone-1

# Example 3: Annotating a tag for better version tracking
git tag -a v2.0 -m "Major release with new features"
```
> **Scenario**: When you release a new version of your project, creating a tag makes it easier to track that specific point in history.

---

## 24. Listing tags with `git tag`
The `git tag` command lists all tags created in the repository.

### Code Examples:

```bash
# Example 1: List all tags in the repository
git tag

# Example 2: List tags that match a pattern (e.g., version numbers)
git tag -l "v*"

# Example 3: Show details of a specific tag
git show v1.0
```
> **Scenario**: Before releasing a new version, you check the existing tags to ensure there are no duplicate version numbers.

---

## 25. Pushing tags to a remote repository
Pushing tags ensures that they are available on the remote repository for collaboration and version tracking.

### Code Examples:

```bash
# Example 1: Pushing a specific tag
git push origin v1.0

# Example 2: Pushing all tags to the remote repository
git push --tags

# Example 3: Pushing annotated tags to the remote
git tag -a v1.1 -m "Annotated release" <commit-sha>
git push origin v1.1
```
> **Scenario**: After tagging a release locally, you push the tags to the remote so collaborators can reference the release.

---

## 26. Fetching tags with `git fetch`
Fetching tags retrieves them from the remote repository without affecting your local branches.

### Code Examples:

```bash
# Example 1: Fetching all tags from the remote
git fetch --tags

# Example 2: Fetch specific tags (if configured for specific branches)
git fetch origin refs/tags/v1.0

# Example 3: Fetch and merge changes including tags
git fetch --all --tags
```
> **Scenario**: A collaborator pushed new tags, and you fetch them to keep your local repository up to date with the latest version markers.

---

## 27. `git -n`
The `-n` option simulates or previews actions without making changes. It can be useful for certain commands to avoid accidental execution.

### Code Examples:

```bash
# Example 1: Preview push changes
git push -n origin main

# Example 2: Simulate branch deletion without actual removal
git branch -d feature-branch -n

# Example 3: Preview rebasing without applying changes
git rebase -n origin/main
```
> **Scenario**: You want to see what will happen when running a push or branch deletion before executing it.

---

## 28. `git -l`
The `-l` option is typically used with listing commands to format the output or filter results.

### Code Examples:

```bash
# Example 1: List all branches
git branch -l

# Example 2: List tags with specific formatting
git tag -l "v*"

# Example 3: List files in the repository
git ls-files -l
```
> **Scenario**: You need a more specific output from Git commands, like when filtering branches or tags.

---

## 29. `git HEAD`
`HEAD` is a reference to the current commit or the tip of the current branch. It is commonly used for checking out specific states or reverting to previous states.

### Code Examples:

```bash
# Example 1: Viewing the commit pointed to by HEAD
git show HEAD

# Example 2: Resetting to the previous commit (HEAD^)
git reset --hard HEAD^

# Example 3: Checking out the latest commit
git checkout HEAD
```
> **Scenario**: You want to return to the state of the last commit or investigate the most recent changes in the branch.

---

## 30. `git diff`
The `git diff` command shows changes between commits, branches, or working directory and staged changes.

### Code Examples:

```bash
# Example 1: Showing unstaged changes in the working directory
git diff

# Example 2: Comparing differences between two branches
git diff main feature-branch

# Example 3: Viewing changes between a commit and the working directory
git diff <commit-sha>
```
> **Scenario**: After making changes, you want to see the difference between your current state and the last commit or another branch.

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
