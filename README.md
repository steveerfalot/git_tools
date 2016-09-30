# git_tools

Some scripts for managing projects comprised of many small repositories

Only works in bash... sorry Windows... unless you are using Git Bash, or the Windows 10 bash-in-windows implementation

Relies on you having [git-up](https://github.com/msiemens/PyGitUp) installed

### Note: The update script is WIP, so use at your own risk

# Usage

## checkout
    
    path/to/script/checkout [name_of_branch_to_checkout]
    
This script will find all git repositories within your current working directory and its subdirectories and `git checkout` whatever branch you pass in

## update *** WIP ***

    path/to/script/update [<optional_base_directory>]
    
This script is not stable, and I don't recommend using it at all.
It attempts to safely delete any branches that have been merged to `master`, but I'm not convinced that it works as intended.

## updateNovo

    path/to/script/updateNovo [<optional_base_directory>]

This script will run `rm -rvf node_modules/ && npm install` in the directory it's executed in, or from the directory you pass to it
Then it finds all git repositories in or under the base directory and runs `git remote prune origin && git up`
If you don't have [git-up](https://github.com/msiemens/PyGitUp) installed, the script will fail

## prune-local
### WARNING: Will delete *** ALL *** branches that aren't master or development

    path/to/script/prune-local [<optional_base_directory>]
    
This script runs `git branch -D` for all branches that are not `master` or `development` in all directories that are git repositories under or in your current working directory or its subdirectories

## reset-hard

    path/to/script/reset-hard
    
Resets all nested git directories with `--hard` <br />
Will support arguments in the future
