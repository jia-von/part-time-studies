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
| `alias ls=\`ls -- color\`` | This `alias` set the `ls` with `color` |  

