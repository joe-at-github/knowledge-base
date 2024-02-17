# Use bash dictionaries

When automating certain tasks, you might start writing one bash function per task.  
Let's assume you are keen to do everything from the command line and have written a set of functions that open specific project pages on Airbrake.

```bash
# /path/to/your/bash/scripts/script-file

function airbrake_project_a {
  open https://<some-custom-domain>.airbrake.io/projects/123
}

function airbrake_project_b {
  open https://<some-custom-domain>.airbrake.io/projects/446
}

```

## What's an alternative?
You can create a dictionary and encapsulate all project ids against their respective project names.

## Here is how it works

Create a dictionary.

```bash
declare -A airbrake_projects=(
  ["project-a"]="123"
  ["project-b"]="456"
)
```

You can then refer to the dictionary like so:

```bash
# /path/to/your/bash/scripts/script-file

# If you are a Mac user.
function airbrake {
  AIRBRAKE_PROJECT_ID="${airbrake_projects[$1]}"
  open https:///<some-custom-domain>.airbrake.io/projects/$AIRBRAKE_PROJECT_ID
}

# If you are a Linux user.
function airbrake {
  AIRBRAKE_PROJECT_ID="${airbrake_projects[$1]}"
  xdg-open https:///<some-custom-domain>.airbrake.io/projects/$AIRBRAKE_PROJECT_ID
}
```

This will allow you to have a neat interface like the one below:
```bash
airbrake project-a
```

## Going one step further

If you find this pattern works for you, you might consider writing more functions relying on dictionaries.
In this case you can choose to encapsulate all your dictionary declarations in a separate file and load them at the top of your script file.

### Script file
```bash
# /path/to/your/bash/scripts/script-file

. /path/to/your/bash/scripts/dictionaries

function airbrake {
  AIRBRAKE_PROJECT_ID="${airbrake_projects[$1]}"
  open https:///<some-custom-domain>.airbrake.io/projects/$AIRBRAKE_PROJECT_ID
}
```

### Dictionary file
```bash
# /path/to/your/bash/scripts/dictionaries

declare -A airbrake_projects=(
  ["project-a"]="123"
  ["project-b"]="456"
)
```