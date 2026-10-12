# Contributing to PowerShell (PowerShell voorbeeld)

Thank you for your interest in contributing to PowerShell.
This document is a short example of how a contribution is prepared, reviewed, and merged.
For the full contributor guide, see [CONTRIBUTING.md](../.github/CONTRIBUTING.md).

## 1. Before you start

* Check the [GitHub issues](https://github.com/PowerShell/PowerShell/issues) to see whether your idea or bug already exists.
* For larger changes, open an issue first so the approach can be discussed.
* Review the [Contributor License Agreement][CLA].

## 2. Set up your environment

1. Fork the repository and clone your fork:

    ```powershell
    git clone https://github.com/<your-github-account>/PowerShell.git
    Set-Location ./PowerShell
    ```

1. Create a feature branch. Never commit directly to `master`:

    ```powershell
    git checkout -b feature/short-description
    ```

## 3. Make your change

* Follow the coding conventions in [.editorconfig](../.editorconfig) and the
  [Coding Guidelines](./dev-process/coding-guidelines.md) where applicable.
* Keep each pull request focused on one change.
* Add or update tests for every behavior change.

## 4. Validate your change

Run the relevant tests before you push:

```powershell
Import-Module ./build.psm1
Start-PSPester -Path ./test/powershell/Language
```

Check that Markdown files pass the repository lint rules defined in [.markdownlint.json](../.markdownlint.json).

## 5. Commit and push

* Write a clear commit message in the imperative mood, for example `Add contribution example`.
* Push your branch to your fork:

    ```powershell
    git push origin feature/short-description
    ```

## 6. Open a pull request

1. Open a pull request against `PowerShell/PowerShell` `master`.
1. Complete the [pull request template](../.github/PULL_REQUEST_TEMPLATE.md).
1. Link the related issue, for example `Fixes #1234`.
1. Respond to review comments and push additional commits to the same branch.

## 7. After merge

* Delete your feature branch from your fork.
* Sync your fork with the upstream `master` branch before you start your next contribution.

[CLA]: https://cla.opensource.microsoft.com/PowerShell/PowerShell
