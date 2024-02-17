# Keeping it tidy

When storing bash variables, aliases and scripts, by default, you might find yourself storing everything in a `.bash_profile` or `.bashrc`.

## Why not store everything in `.bash_profile` or `.bashrc`?

- While this may be quick and easy, it might over time be less readable, easy to work with and difficult to extend.
- You might be a freelancer working on different projects and needing more encapsulation in the script you use.
- You may want to isolate scripts and aliases you use for work from the ones you use for personal projects and personal use so you can easily discard domain specific scripts that are no longer needed should your work situation change.
- You might also want to keep variables needed to run and install various packages and libraries in a different file so you can more easily keep track of what is installed or out of date.

## What's an alternative?

Let's assume you are working with `.bash_profile` and you create the folder structure below.

## Folder structure
```bash
/path/to/your/bash/scripts
├── personal
│   ├── .profile
│   └── bin
│       └── # Custom executables go here.
└── work
    ├── .profile
    └── bin
        └──  # Custom work executables go here.
```

## .bash_profile
```bash
# Load custom scripts.
. /path/to/your/bash/scripts/personal/.profile
. /path/to/your/bash/scripts/personal/.profile

# Install related variables go here, examples below.

# zsh
export BASH_SILENCE_DEPRECATION_WARNING=1

# rbenv
eval "$(/opt/homebrew/bin/brew shellenv)"
eval "$(rbenv init - bash)"

# ImageMagic
export PATH="/opt/homebrew/opt/imagemagick@6/bin:$PATH"
```

## personal/.profile
```bash
# Add your custom executables to PATH.
export PATH="/path/to/your/bash/scripts/personal/bin:$PATH"

# Personal aliases, functions and variables go here.
```

## work/.profile
```bash
# Add your work related executables to PATH.
export PATH="/path/to/your/bash/scripts/work/bin:$PATH"

# Work related aliases, functions and variables go here.
```