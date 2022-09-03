# Contributing to the windows-playbook

Want to contribute? Great! First, read this page.

## How to become a contributor

- Direct contributions
  - **Create pull requests directly.**
  - Please send e-mails to nabokikh@duck.com if you have any questions.
- Feedback suggestions and bugs.
  - We use GitHub issues to track bugs and features.
  - For bugs and general issues please [file a new issue](https://github.com/AlexNabokikh/windows-playbook/issues/new).

## Code contribution guidelines

### Conventional commits

- Use [Conventional Commit](https://www.conventionalcommits.org/en/v1.0.0/#summary) message syntax for repo auto-tagging and releasing via pipeline.

### Code style and conventions

- Use [Ansible lint](https://github.com/ansible/ansible-lint) and [YAML lint](https://github.com/adrienverge/yamllint) to check code style.
- Respect the `.ansible-lint` and `.yamllint.yml` files specified in the source tree.

### Fix wrong commit

In case you have an issue with your commit it is possible to fix it with `git commit --amend`.

In case the errored commit is not the last one it is possible to fix it with the following procedure:

```shell
git rebase --interactive 'bbc643cd^'
```

Please note the caret `^` at the end of the command, because you need actually to rebase back to the commit before the one you wish to modify.

In the default editor, modify `pick` to `edit` in the line mentioning `'bbc643cd'`.

Save the file and exit: git will interpret and automatically execute the commands in the file. You will find yourself in the previous situation in which you just had created commit `bbc643cd`.

At this point, `bbc643cd` is your last commit and you can easily amend it to change the text with the command:

```shell
git commit --all --amend
git rebase --continue
```
