# Portability
When using custom files to store functions and scripts, you might place them into your home directory and load them via your bash_profile, hardcoding their paths.

```bash
# .bash_profile
. /Users/<username>/path/to/scripts
```

## Why not hardcoding paths to custom scripts?
If you are storing scripts in version control and reusing them across different machines, you might have different usernames per machine and therefore a different location for your home directory.

In this scenario, you would have to manually replace all instances of your username to suit the folder structure of the machine you are working on.

## What's an alternative?
Adopt a predictable folder structure and refer to your home directory using the `$HOME` variable.

```bash
. $HOME/path/to/scripts
```