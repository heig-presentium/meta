# Contributing

We would love your input! We want to make contributing to this project as easy and transparent as possible, whether it is:

- Reporting a bug
- Discussing the current state of the code
- Submitting a fix
- Proposing new features

> [!IMPORTANT]
> Contributions you make to this project are understood to be under the same [MIT License](https://choosealicense.com/licenses/mit/) that covers the project.

## Contribution Workflow

Our process uses the [GitHub flow](https://guides.github.com/introduction/flow/), so all code changes happen through pull requests.

1. Fork the repository
2. Create a new branch based off the **main** branch
3. Make your changes
4. If you've added code that should be tested, add tests
5. If you've changed APIs, update the documentation
6. Ensure the test suite passes and that the code lints
7. Commit your changes, and push
8. Submit a pull request! If more work is needed, make sure to report it as a draft pull request

> [!NOTE]
> When pushing a commit, create a _draft pull request_ **immediately** to indicate that the work is in progress and others can see it.
> When the work is ready for review, mark the pull request as _ready for review_.

### Reviewing a Pull Request

#### Addressing review feedback

If we ask for changes via code reviews:

1. Make the changes to your code in your branch

2. Re-run the test suites to ensure that the changes did not break anything

3. Create a **fixup** commit and push it to your branch.
    
    ```bash
    git commit --fixup <commit-hash>
    git push origin <branch-name>
    ```

That's it! The pull request will be updated with the new changes.

#### Updating the Commit Message

Whether for adhering to our commit message convention, or simply to make the commit message more descriptive, we might ask you to update the commit message.
In this case, you can use the following method:

1. Amend the last commit message

    ```bash
    git commit --amend
    ```

2. Force push the changes to the branch

    ```bash
    git push --force-with-lease
    ```

> [!TIP]
> If you need to update the commit message of a commit that is not the last one, you can use the `git rebase` command in interactive mode.
> See the [git docs](https://git-scm.com/docs/git-rebase#_interactive_mode) for more details.

## Coding Rules

### Styling

To ensuire consistency throughout the source code, keep these rules in mind as you are working:

- All features or bug fixes **must be tested** by one or more tests

- All public API methods **must be documented**

- For JavaScript, Typescript, and Vue files, we follow the **prettier** code style along with **eslint** rules. Run `nr lint` to check your code.

- For Java files, we follow the **Google Java Style Guide**. Run `./gradlew check` to check your code.

### Commit Message Format

We have very precise rules over how our git commit messages can be formatted. This leads to more readable messages that are **easy to follow** when looking through the **project history**. What is described below is largely inspired by Angular's commit message convention, and is checked by the `commitlint` tool.

Each commit message consists of a **header**, a **body**, and a **footer**.

```
<header>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The `<header>` is mandatory and must conform to the [Commit Message Header](#commit-message-header) format.

The `<body>` is optional and can contain a more detailed description of the commit. If present, it must conform to the [Commit Message Body](#commit-message-body) format.

The `<footer>` is optional. The [Commit Message Footer](#commit-message-footer) format describes what it is used for and the structure it must have.

This standard is verifed by the `commitlint` tool, which is run automatically when you commit changes.

#### Commit Message Header

```
<type>(<scope>): <short summary>
  │       │             │
  │       │             └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       │
  │       └─⫸ Commit Scope (optional)
  │
  └─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

The `<type>` and `<summary>` fields are mandatory, the `(<scope>)` field is optional.

##### Type

Must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- **ci**: Changes to our CI configuration files and scripts (examples: CircleCi, SauceLabs)
- **docs**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **test**: Adding missing tests or correcting existing tests

##### Scope

The scope should be the name of the package / part of the project that is being changed.

##### Summary

Use the summary field to provide a succinct description of the change:

- use the imperative, present tense: "change" not "changed" nor "changes"
- don't capitalize the first letter
- no dot (.) at the end

#### Commit Message Body

Just as in the summary, use the imperative, present tense: "fix" not "fixed" nor "fixes".

Explain the motivation for the change in the commit message body. This commit message should explain _why_ you are making the change.
You can include a comparison of the previous behavior with the new behavior in order to illustrate the impact of the change.

#### Commit Message Footer

The footer can contain information about breaking changes and deprecations and is also the place to reference GitHub issues, Jira tickets, and other PRs that this commit closes or is related to.
For example:

```
BREAKING CHANGE: <breaking change summary>
<BLANK LINE>
<breaking change description + migration instructions>
<BLANK LINE>
<BLANK LINE>
Fixes #<issue number>
```

or

```
DEPRECATED: <what is deprecated>
<BLANK LINE>
<deprecation description + recommended update path>
<BLANK LINE>
<BLANK LINE>
Closes #<pr number>
```

Breaking Change section should start with the phrase "BREAKING CHANGE: " followed by a summary of the breaking change, a blank line, and a detailed description of the breaking change that also includes migration instructions.

Similarly, a Deprecation section should start with "DEPRECATED: " followed by a short description of what is deprecated, a blank line, and a detailed description of the deprecation that also mentions the recommended update path.

### Revert commits

If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit.

The content of the commit message body should contain:

- information about the SHA of the commit being reverted in the following format: `This reverts commit <SHA>`,
- a clear description of the reason for reverting the commit message.
