# Use separate git config files

While working on different projects (e.g., work and personal projects), you might find yourself switching between different github accounts, a github account and a bitbucket account, etc.

In this scenario, you will have to manually switch git user details to make sure you are using the right user for a given project.

## What's an alternative?
- Adopt a predictable folder structure, allowing you to clearly separate projects based on their context (e.g., work, personal projects, etc.).
- Encapsulate the config that is shared across all git users in `~/.gitconfig` and create a separate config per git user.
- Load the relevant configuration based on which folder you are working from.

## Here is how to do it.

Let's assume you keep all work-related repositories in `~/work` and personal projects-related repositories in `~/personal-projects`.

Edit your `~/.gitconfig` to use the following content:

```
# ~/.gitconfig
[includeIf "gitdir:~/personal-projects/"]
  path = .gitconfig-personal-projects
[includeIf "gitdir:~/work/"]
  path = .gitconfig-work
```

Create a `~/.gitconfig-personal-projects` pointing to the user details for personal projects.

```
# ~/.gitconfig-personal-projects
[user]
  name = <your user name>
  email = <your email>
```

Create a `~/.gitconfig-personal-projects` pointing to the user details for work-related repositories.

```
# ~/.gitconfig-work
[user]
  name = <your user name>
  email = <your email>
```

