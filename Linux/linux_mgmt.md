# Linux Management

## The Shell Environment
Customize and use environment variable is important. Environment variables are represented capital letters. `ENVVAR=value;export ENVVAR`. 

**Note**:
- Environment variable set is local to the shell. Opening other shell to try to view the same environment variable, the shell will not understand the set variable. Environment variable is set locally to the specific shell by default. 

Commands
| Commands | Description |
| --- | --- |
| `Ctrl`+`Alt`+`t` | To open shell terminal |
| `$` | The `$` is essential because it shows that it is an environment variable |
| `echo  $HOME` | Show the value within HOME variable |
| `MYVAR=123` | To set the env variable `MYVAR` with value `123` |
| `export MYVAR` | Export `MYVAR` variable to the children of the shell. Therefore the environment variables is available to used by other shells. `export` also make the env variable global and available to use by other software. |
| `MYVAR=123 ; export MYVAR` | A more concise way to create and export env variable. |
| `bash` | To open a new variable. By default using `bash` will open a shell within a shell |
| `unset MYVAR2` | To unset the environment variable of `MYVAR2` |

## Standard Environment Variables

| Variable name | Description |
| --- | --- |
| `HOSTNAME` | Current hostname (TCP/IP) of the computer |
| `USER` | Current user name |
| `HOME` | Home directory of the current user and can be also represented by `~` |
| `PS1` | Default bash shell prompt |
| `LD_LIBRARY_PATH` | Directories that contain libraries |
| `PATH` | List of locations the OS searches for executables | 
| `MANPATH` | List of directories searched for man (manual) pages |
| `TMPDIR` | Current temp directory |
| `LANG` | Current language in use |

To investigate the current environment define.

| Command | Description |
| --- | --- |
| `env` | The standalone `env` produces long outputs that might be confusing. Therefore piping with `|` and `grep` produces a more concise output |
| `env | grep SESSION` | Searches and show environment variables that include `SESSION` | 
| `|` | This is a pipe command |

## Aliases

| Command | Description |
| --- | --- |
| `ls` | Example of an alias, `ls` |
| `alias` | `alias` is use to represent a other command. Especially commands that is repetitive | 
| `alias ls='ls -- color'` | This `alias` set the `ls` with `color` |  
| `alias cya='exit'` | The `cya` becomes an `exit` command |
| `ls -a` | Regular `ls` show regular file, the `-a` shows the hidden files |

# Configuration File Locations

In order to use/define set environment variable esepcially in every login, user, and the whole computer globally, set the environment variable within `/etc/profile` or `/etc/profile.d/*`. Alternatively, it can be in `/etc/bashrc` or `/etc/bash.bashrc`. Different distribution uses different naming conventions, therefore these differences as described. 

## For single user configurations
Under the user `home` directory, set the user specific environment variable. These can be set in:

| Directory | Description |
| --- | --- |
| `~/.bash_login` | Script executed when user login. Use `vi .bash_login` to edit the file |
| `~/.profile` | `~/.profile` is a legacy system, similar to `/etc/profile` and `/etc/profile.d` |
| `/.bash_profile` | n/a |
| `~/.bashrc` | n/a |
| `~/.bash_logout` | Script that is executed whenever user logout |
| `.` | `.` in front of the file means it is a hidden file |

## Source Command
- When setting environment variable, be careful about the scope of environment variable. 

- Whenever a shell script runs, Linux will open a new shell and execute the shell script. When the shell script ends, the shell closes and everything will go back as it was before. 

| Command | Description |
| --- | --- |
| `vi demoenv.sh` | `vi` command create a shell script `demoenv.sh` |
| `sh demoenv.sh` | `sh` command runs the `demoenv.sh` shell script |
| `source demoenv.sh` | `source` command will ensure that the script is run within the current shell |
| `. demoenv.sh` | `.` command is identical to `source` command |



