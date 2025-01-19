# 🌳 Branching Policy

This document outlines the branching strategy for our organization to ensure a consistent and organized approach to managing development efforts.

---

## 🛠️ **Branch Naming Convention**

All branches must follow this naming pattern:  
```text
{taskType}/{taskId}
```

### 🔤 **Components**

1. **`taskType`**  
   - Represents the type of work being done.
   - Allowed values:
     - `feature` – For new features.
     - `bugfix` – For fixing bugs.
     - `hotfix` – For urgent production fixes.
     - `chore` – For maintenance or miscellaneous tasks.
     - `test` – For adding or updating tests.
     - `docs` – For documentation updates.

2. **`taskId`**  
   - The unique identifier for the related task or issue.
   - This could be the ticket number from a task tracker (e.g., Jira, Trello, GitHub Issues).

#### Example Branch Names
- `feature/1234` – A new feature related to issue #1234.
- `bugfix/5678` – A bug fix related to issue #5678.
- `hotfix/9876` – An urgent production fix for issue #9876.
- `docs/4321` – Documentation updates for issue #4321.

---

## 🌟 **Best Practices**

### 🏷️ **General Rules**
- Use **lowercase** letters for `taskType`.
- Separate the `taskType` and `taskId` with a `/`.
- Avoid spaces or special characters in branch names.

### 🔒 **Branch Protection**
- Protect the main branches (e.g., `main`, `develop`) by enabling:
  - Code reviews with at least one approver.
  - Status checks before merging.
  - Commit history linearization (squash or rebase merges).

### 🔄 **Branch Lifecycle**
1. **Create a Branch**  
   Always branch from `main` or `develop` (depending on your workflow):
   ```bash
   git checkout main
   git checkout -b {taskType}/{taskId}
   ```

2. **Work on the Task**  
   Commit regularly, following the [Commit Message Policy](#✨-commit-message-policy).

3. **Merge the Branch**  
   - Once the work is complete, open a Pull Request (PR) and ensure:
     - All tests pass.
     - Code reviews are approved.
   - Delete the branch after merging to keep the repository clean.

---

## 🗂️ **Branch Workflow**

### 🔀 **Main Branches**
- **`main`**  
  - The production-ready branch.
  - Contains only tested and stable code.
- **`develop`**  
  - The integration branch for ongoing development.
  - Merges from feature or bugfix branches happen here.

### 🌱 **Supporting Branches**
- **Feature Branches**  
  Used to develop new features:  
  ```text
  feature/{taskId}
  ```
- **Bugfix Branches**  
  Used to fix known issues:  
  ```text
  bugfix/{taskId}
  ```
- **Hotfix Branches**  
  Used for urgent fixes to the production environment:  
  ```text
  hotfix/{taskId}
  ```
- **Chore Branches**  
  Used for maintenance and refactoring:  
  ```text
  chore/{taskId}
  ```
- **Documentation Branches**  
  Used for documentation updates:  
  ```text
  docs/{taskId}
  ```

---

## 🚀 **Pull Request Guidelines**

- Ensure your branch is up-to-date with the target branch:
  ```bash
  git pull origin {target-branch}
  ```
- Follow the [Commit Message Policy](/commit.policy.md).
- Use descriptive PR titles and link related issues.
- Request a review from the appropriate team members.

#### Example Pull Request Title
```text
[Feature] Add login functionality (#1234)
```

---

## ⚙️ **Tools for Enforcement**

### 🔄 **Automation**
Integrate tools like the following to enforce branch naming rules:
- **Git Hooks**:
  Use a pre-push hook to validate branch names:
  ```bash
  # .git/hooks/pre-push
  branch_name=$(git symbolic-ref HEAD 2>/dev/null | cut -d'/' -f3-)
  if [[ ! $branch_name =~ ^(feature|bugfix|hotfix|chore|test|docs)/[0-9]+$ ]]; then
      echo "Error: Branch name does not follow the required pattern {taskType}/{taskId}."
      exit 1
  fi
  ```
- **GitHub Actions**:
  Add a workflow to check branch names on PRs.

---

By following this branching policy, we ensure a clean, predictable, and efficient workflow for all team members. 🚀