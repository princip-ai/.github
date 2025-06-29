# ✨ Commit Message Policy

This document outlines the commit message style guide for our organization, based on the **Conventional Commit** standard. Following this policy ensures that our commit history is consistent, easy to read, and useful for automation and changelogs.

---

## 🏷️ **Commit Message Structure**

Each commit message should follow this structure:

```text
<type>(<taskId>): <short description>

<body>

<footer>
```

---

## 🔑 **Key Components**

### 🔤 **Type**
The type indicates the purpose of the commit. Use one of the following:

| Type       | Meaning                                      | Example                   |
|------------|----------------------------------------------|---------------------------|
| **feat**   | A new feature                                | `feat(taskId): add login`   |
| **fix**    | A bug fix                                    | `fix(taskId): resolve button issue` |
| **chore**  | Miscellaneous tasks or maintenance work      | `chore: update dependencies` |
| **docs**   | Documentation updates or changes             | `docs(taskId): update usage section` |
| **style**  | Code style changes (formatting, no logic)    | `style(taskId): update navbar styles` |
| **refactor** | Code refactoring without functional changes | `refactor(taskId): optimize query` |
| **test**   | Adding or modifying tests                   | `test(taskId): add unit tests` |
| **ci**     | Continuous integration changes              | `ci: update GitHub Actions` |

---

### ✍️ **Short Description**
- Use an **imperative tone** (e.g., "add", "update", "fix").
- Keep it **concise** (72 characters max).
- Start with a lowercase letter (unless it's a proper noun).

Example:
```text
fix(DEV-2210): handle missing user ID in response
```

---

### 📜 **Body (Optional)**
The body provides more detailed information about the changes. It should:
- Explain the **why** behind the change.
- Additional details about the changes.
- Wrap text at 72 characters for readability.

Example 1:
```text
feat(DEV-2210): add OAuth2 support

This feature allows users to log in using OAuth2. It includes
support for Google and Facebook authentication providers.
```

Example 2:
```text
feat(DEV-2211): refactor OAuth

- Added feature flag for restrinction
- Added logic layer for authentication process
```

---

### 📝 **Footer (Optional)**
Include additional metadata such as:
- Links to related issues or tickets (`DEV-2210`).
- **BREAKING CHANGE**: Describe any backward-incompatible changes.

Example:
```text
BREAKING CHANGE: The auth module now requires an OAuth2 secret key.
```

---

## 🌟 **Examples**

### ✅ Good Commit Messages
- `feat(taskId): add dark mode toggle`
- `fix(taskId): handle token expiration`
- `docs(taskId): add contributing section`
- `chore: update project dependencies`
- `refactor(taskId): optimize user query`

### ❌ Bad Commit Messages
- `update code` (Too vague)
- `fix bug` (No scope or description)
- `new feature added` (Wrong format)

---

## 🚀 **Automation Integration**
This policy aligns with tools like **commitlint** and **semantic-release** for:
- Enforcing commit message rules.
- Generating changelogs.
- Managing versioning automatically.

---

## 🎯 **Best Practices**
- Write meaningful commits.
- Commit often, but keep them small.
- Use the correct type and scope for clarity.

By following this policy, we maintain a clean and structured commit history that benefits everyone!