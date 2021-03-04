# Linux Management

## The Shell Environment
Customize and use environment variable is important. Environment variables are represented capital letters. `ENVVAR=value;export ENVVAR`. 

**Note**:
- Environment variable set is local to the shell. Opening other shell to try to view the same environment variable, the shell will not understand the set variable. Environment variable is set locally to the specific shell by default. 

Commands
| Commands | Description | Example |
| --- | --- | --- |
| `Ctrl`+`Alt`+`t` | To open shell terminal | n/a |
| `echo  $HOME` | Show the value within HOME variable | n/a |
| `MYVAR=123` | To set the env variable `MYVAR` with value `123` | n/a |
| `export MYVAR` | Export `MYVAR` variable to the children of the shell. Therefore the environment variables is available to used by other shells | n/a |
| `MYVAR=123 ; export MYVAR` | A more concise way to create and export env variable | Export makes it global |
| `bash` | To open a new variable. By default using `bash` will open a shell within a shell | n/a |
| `unset MYVAR2` | To unset the environment variable of `MYVAR2` | n/a |