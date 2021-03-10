# Linux Management

## Customize and Use the Shell Environment
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

### Standard Environment Variables

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

### Aliases

| Command | Description |
| --- | --- |
| `ls` | Example of an alias, `ls` |
| `alias` | `alias` is use to represent a other command. Especially commands that is repetitive | 
| `alias ls='ls -- color'` | This `alias` set the `ls` with `color` |  
| `alias cya='exit'` | The `cya` becomes an `exit` command |
| `ls -a` | Regular `ls` show regular file, the `-a` shows the hidden files |

### Configuration File Locations

In order to use/define set environment variable esepcially in every login, user, and the whole computer globally, set the environment variable within `/etc/profile` or `/etc/profile.d/*`. Alternatively, it can be in `/etc/bashrc` or `/etc/bash.bashrc`. Different distribution uses different naming conventions, therefore these differences as described. 

### For single user configurations
Under the user `home` directory, set the user specific environment variable. These can be set in:

| Directory | Description |
| --- | --- |
| `~/.bash_login` | Script executed when user login. Use `vi .bash_login` to edit the file |
| `~/.profile` | `~/.profile` is a legacy system, similar to `/etc/profile` and `/etc/profile.d` |
| `/.bash_profile` | n/a |
| `~/.bashrc` | n/a |
| `~/.bash_logout` | Script that is executed whenever user logout |
| `.` | `.` in front of the file means it is a hidden file |

### Source Command
- When setting environment variable, be careful about the scope of environment variable. 

- Whenever a shell script runs, Linux will open a new shell and execute the shell script. When the shell script ends, the shell closes and everything will go back as it was before. 

| Command | Description |
| --- | --- |
| `vi demoenv.sh` | `vi` command create a shell script `demoenv.sh` |
| `sh demoenv.sh` | `sh` command runs the `demoenv.sh` shell script |
| `source demoenv.sh` | `source` command will ensure that the script is run within the current shell |
| `. demoenv.sh` | `.` command is identical to `source` command |
| `exec` | `exec` command will open the script, run the script, replace the current shell, and finally terminate/close the shell after finish executing |

### Skeleton Directory for New Users
`/etc/skel` is the directory which stores *template* for creating new user files. Whenever a new user is created, `/etc/skel` will be copied to create new user directories.

### Set the PATH

| Command | Description |
| --- | --- |
| `echo $PATH` | Shows the `PATH` of the current directory |

## Customize or Write Simple Scripts
- Shell script does not have compiler, it is just a text file.
- The first line of any shell script defines the shell in which it should run.  
- **Shebang**: `#!` also called the **hashbang** or **poundbang**.

| Shell Type | Description | Shebang |
| --- | --- | --- |
| `(sh)` | Bourne shell goes back to the begining of UNIX, directory `/bin/sh` |  `#!/bin/sh` |
| `(bash)` | Bourne again shell, `/bin/bash` | `#!/bin/bash` |
| `(csh)`, `(ksh)`, `(tcsh)`, `(zch)` | Other type of shell |  |

| Command | Description | Example |
| --- | --- | --- |
| `Do it` | Change mode chmod | `chmod a+x scriptName` |
| `sh scriptName` | launches a new shell and immediately execute the script |  | 

### How to write scripts
# 
#### Easy mode
- The easy mode is to just use a **generic script** that simulates typing the command.
  - Type commands into a `.txt` file
  - In simple scripts, it is common to use complete paths so you do not ever have any relative pathing.
  - Use the `&` at the end of a command (so you don't have to wait).
  - If you typed in a command and went to the next row and typed another command, then the first command woud have to be complte before the second command would execute. 
  - `demo.sh &` sends it to the background. 
# 
#### To use variables in script

| Type | Description | Example |
| --- | --- | --- |
| Positional | Depend on the position of the arguement when the script goes and run. `$1`, `$2`, `$3` is the position number | `$1Do it A` `$2Do it B` `$3Do it C` |
| Named variables |  |  |
| `gedit` | Launch the `gedit` editor |  |
| `PATH=~/scripts:$PATH` | `:` is to seperate previous directory from the next |  |
| `chmod u+x *.sh` | Change execute command to change privilege. `u+x` means user executable |  |
#
#### Conditional Expressions

| Statement | Description | Example |
| --- | --- | --- |
| `If` | If the statement is **True** commands after `Then`. If statement is **False** commands after `Else` | `if test conditionalExpression then commands else commands fi` or `if [ conditionalExpression ] then commands else commands fi` | 
| `-f` | Test to see if file exists |  |
| `-s` | Test to see if file exists and size > 0 |  |
| `String 1 = String 2` | Comparing String 1 and String 2 |  |

If there is many expressions use `Case` statement instead. 

```
Case string in
    pattern1 ) command ;;
    pattern2 ) command ;;

esac
```
where the `string` matches against `pattern1` or `pattern2`.
- use quotation marks to make two words into one arguement, eg. `"hot dog"`.
#
#### Reptition Structures
A structure or a group of commands that are executed more than once. There are two kind of repition structures:
- `For` loop
   - `for var in list do`
   - A `ls` is any space-separated string of values
   - If a example file `demo2.sh~`, when the `~` is at the end of the file name, represents previous version of the file. `gedit` save older version of the file with `~`.
```
for i in $(ls); do
    echo file: $i
done
```
or

```
for i in seq '1 10' ;
do
    echo $i
done
```
- The `seq` takes two arguements; beginning and ending

- `While` loop
   - `while [condition] do`
   - `-lt` means less than, `-le` means less than or equal

```
i=0

while [ $i -lt 10 ]
do
    echo "The counter is $i"
    i=$(( $i + 1))
done
```
#
#### Functions
- Track and return values
- A section of code that can be called by a specific name
  - To be used if statements that are executed over and over again
  - Makes scripts look cleaner

```
functionName(){
    commands
}
```
Example of a function

```
quit(){
    exit
}
disp(){
    echo $i
}

disp Hello
disp World
quit
echo "Never gets here!"
```
Notes:
- Keep shell scripts as simple as possible
  - more complex scripts have more places to break down.
- Use command substitution
  - Example `for i in ls*.sh`
- Test for return values for success or failure or other information provided by a command
  - Most commands return negative numbers to indicate errors; negative value means some sort of error, positve value report some sort of status

#
**Callee** and **Caller** script.

`democallee.sh` script
```
exit -1
```

`democaller.sh` script
```
if ! ./democallee.sh ; then
    echo "callee.sh returned an error!"
fi
```

#### Read input from the User
**Read** statement to get/prompt data.
```
echo "Enter a name: "
read name

echo "Hello, "$name"!"
```

Notes:
- Run commands
- Make decisions
- Iterate over many commands 
- Test out various statuses