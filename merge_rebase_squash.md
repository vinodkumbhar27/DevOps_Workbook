Git Merge, Git Rebase, and Git Squash Commit are three different techniques used in Git version control to incorporate changes from one branch into another. Each has its own use cases and scenarios. Let's explore each of them:

### 1. Git Merge:

**Definition:**
- Git Merge is a command used to integrate changes from one branch into another.
- It creates a new commit, often referred to as a "merge commit," that combines the changes from the source branch into the target branch.

**Usage:**
- Typically used for integrating feature branches into the main branch (e.g., merging a feature branch into the `master` branch).
- It preserves the commit history of both branches.

**Scenario:**
- You have a feature branch where you've developed a specific feature, and you want to integrate it into the main branch.

**Command:**
```bash
# While on the target branch (e.g., master)
git merge feature-branch
```


![image](https://github.com/discover-devops/DevOps_Workbook/assets/53135263/2934676e-3e14-450a-9e4a-8fc8ffcda56e)


### 2. Git Rebase:

**Definition:**
- Git Rebase is a command used to move or combine a sequence of commits to a new base commit.
- It essentially rewrites the commit history, making it linear.

**Usage:**
- Useful for cleaning up the commit history and creating a more linear and cleaner history.
- Can be used to incorporate changes from one branch into another, similar to merge but with a different commit history.

**Scenario**:
You start working on a new feature in a branch called dev while the main project development continues on the main branch.

**Starting Point**:
**main branch commits**: A → B → C
**dev branch commits**: A → D → E
Here, A is the point where both branches were the same last time. Commits B and C are new updates to the main project, and D and E are your work on the new feature.

**Goal**:
You want to update your dev branch so it includes all the recent updates from main, but you also want to maintain a clean, linear history.

**Action**: Rebase dev on main
**What happens during a rebase**:

Git "lifts" the unique commits from your dev branch (D and E) off the base commit (A).
It then places these commits (D and E) on top of the latest commit on main (C).

**Result After Rebase**:
**main branch commits**: A → B → C
**dev branch after rebase**: A → B → C → D' → E'
After rebasing, commits D' and E' are the rebased versions of D and E. They may be the same or slightly different if adjustments were needed to fit on top of C. The history now appears as if you started your feature development right after the latest update in main, creating a straightforward, linear sequence of events.


![image](https://github.com/discover-devops/DevOps_Workbook/assets/53135263/0ade2d04-f651-4df8-a6db-71a45f7f2837)



### 3. Git Squash Commit:

**Definition:**
- Git Squash is a technique used to combine multiple commits into a single commit.
- It condenses the commit history, making it easier to understand.

**Usage:**
- Useful when you have a series of small, incremental commits in a feature branch that you want to combine into a single, meaningful commit before merging it into the main branch.

**Scenario:**
- You've made several small commits during the development of a feature, and before merging it into the main branch, you want to combine them into a single, well-documented commit.

**Command:**
```bash
# While on the feature branch
git rebase -i HEAD~n
```
After running the above command, you can choose to squash or fixup commits interactively.

![image](https://github.com/discover-devops/DevOps_Workbook/assets/53135263/85ab8478-beca-4638-89d5-81383ca37b16)



### How these are related:

- **Git Merge vs. Git Rebase:**
  - Both are used to integrate changes from one branch into another, but they do it in different ways.
  - Merge creates a new commit, preserving the commit history of both branches.
  - Rebase moves or combines commits, creating a linear history.

- **Git Rebase vs. Git Squash:**
  - Both involve rewriting commit history.
  - Rebase restructures the existing commits, while Squash combines multiple commits into one.

- **Git Merge vs. Git Squash:**
  - Merge integrates changes from one branch into another, preserving the original commit history.
  - Squash combines multiple commits into one, creating a cleaner and condensed history.

### When to apply what:

- **Use Git Merge when:**
  - You want to integrate changes from one branch into another and preserve the commit history.
  - It's a straightforward integration, and a merge commit is acceptable.

- **Use Git Rebase when:**
  - You want to maintain a clean, linear commit history.
  - You want to incorporate changes from one branch into another without creating merge commits.
  - It's a personal or feature branch, and you want to update it with changes from the main branch.

- **Use Git Squash when:**
  - You have a series of small, incremental commits that you want to combine into a single, well-documented commit before merging.
  - You want to keep the commit history concise and meaningful.

In summary, the choice between Git Merge, Git Rebase, and Git Squash depends on your workflow, the structure of your team, and the desired commit history in your project. Each has its own advantages and trade-offs, and the decision should be based on the specific requirements of your project.
