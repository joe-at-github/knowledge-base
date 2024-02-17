# A more visual output of `git log`

When working on a repository, you might need to clearly understand what changes have occurred over time. For example, you might need to track any changes made in relation to a given feature to locate relevant merge commit hashes and access their associated pull requests.

You could simply use `git log` to output the entire git history and manually scroll through it, but it might be hard to find what you are looking for.

## What's an alternative

You can pass extra flags and parameters to `git log` to output a more synthetic view of the git history.

## Here is how it works

- Use the `graph` flag to get a visual representation of which branch a commit was introduced by and when and where branches were merged.
- Use the `pretty` flag to make the output even clearer to read.
- Use the `abbrev-commit` flag to make sure you are not submitting the whole commit but simply its title.
- Use the `date` flag with'relative` to quickly understand how long ago the change occurred.

```bash
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

## Going one step furter

If you find this format works for you, you might want to use it consistently using a git alias.
To do so, simply add this extra config to your `~/.gitconfig`:

```
# ~/.gitconfig

[alias]
  graph = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
```

This will allow you to use the interface below:

```
git graph
```