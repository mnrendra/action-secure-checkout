
# Contributing Guidelines

Thank you for considering contributing to this project! We appreciate your help in making this project better. Please follow the guidelines below to ensure that your contributions are smoothly integrated.

## Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](./CODE_OF_CONDUCT.md). Please engage respectfully and constructively.

## How to Contribute

### 1. Start a Discussion

Begin by [opening a discussion](/discussions) to propose your changes or improvements. We’ll invite you as [contributors](/graphs/contributors) and assist you in creating the corresponding [issue](/issues) and working [branch](/branches) for your contribution.

### 2. Set Up Your Local Environment

Follow these steps to prepare your development environment:

- Clone the repository using SSH:
  ```bash
  git clone git@github.com:mnrendra/action-secure-checkout.git
  ```

- Navigate to the project directory:
  ```bash
  cd action-secure-checkout
  ```

- Switch to the assigned branch:
  ```bash
  git checkout [assigned-branch-name]
  ```

- Verify your Git configuration to ensure that your commits are associated with the correct author information:
  ```bash
  git config --list
  ```
  *Verify that `user.name` is your name and `user.email` is your [private email](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address).*

### 3. Make Your Changes

Follow these guidelines to implement your changes:

- Maintain code readability and consistency by providing proper documentation.
- Avoid introducing breaking changes to the public API or major behavioral changes unless discussed in advance. We are following semantic versioning, so please follow its guidelines.
- Update the [`README.md`](./README.md) file to reflect any changes to public APIs, usage examples, or configuration options introduced by your contribution.
- Keep commits atomic and focused on a single change.

### 4. Commit Your Changes

We follow [Conventional Commits](https://github.com/pvdlg/conventional-commit-types). Use the format:

- Run the commit cli properly:
  ```bash
  git commit -m "[type]: [message]"
  ```

- Use a valid [commit type](https://github.com/pvdlg/conventional-commit-types).
- Include the related issue number.
- Match your commit scope to the branch name if applicable.
- Avoid breaking changes unless approved beforehand.

> ⚠️ Pull requests with non-standard or poorly formatted commit messages will be **rejected**.

### 5. Push Your Changes

Ensure that your local branch is up-to-date with the base branch before pushing it to the remote repository:
```bash
git pull --rebase origin [base-branch]
```
> ⚠️ Please only pull from the **base branch** (e.g., `dev`) — do not pull from any other branches.

Push your up-to-date local branch to the remote repository:
```bash
git push origin [assigned-branch-name]
```

### 6. Submit a Pull Request

Create a Pull Request targeting the base branch (e.g., `dev`). After submission, a maintainer will review it before merging. Please use the following format for your Pull Request:

#### Pull Request Title
Must match the related issue title (e.g., `feat: something`).  

#### Pull Request Description
Use the following template to ensure consistency:  
```
issues:
* [issue title] (#[issue number])

commits:
* [commit title] ([first 7 chars of the commit hash])
```
Example:  
```
issues:
* feat: something (#123)

commits:
* feat: something (abc123d)
```

See [merged commits](/commits/main/) for reference.

#### Ensure that the Pull Request Includes:
- Correct **target branch**
- Relevant **reviewers**
- Proper **assignee**
- Updated **project status**
- Linked **issue**

If you have any questions, feel free to [open a discussion](/discussions). We’re here to help!

Thank you for your contributions and collaboration!

## Maintainer
[@mnrendra](https://github.com/mnrendra)
