# Introduction to the Terminal

The terminal is an application that allows the user to interact directly with the shell by writing commands

## Terminal Life-cycle

1. **Open/Init:** Opening the terminal, loading the environment variables ($PATH, $LOCALE, etc.) and running the shell init script (eg. ~/.bashrc)
2. **Operation:** Pass input commands to the shell to be executed and display the results
3. **Close:** Save all commands used during the session to the history file and run the shell exit script (eg. ~/.bash_logout)

## Commands

- `env`: Run a command in a modified variable

# Bash Script Basics

## Shebang

At the start of each bash script, a shebang `#!` is insterted to let the executor now what install to execute this with

```
#! /path/to/shell
```

## Inputs

### Positional Paramters

You can pass arguments to the script from the command line at the time of execution and then refer to them from within the script like follows

```
# Script name
$0

# First argument
$1

# Second argument
$2

# and so on...
```

### User Input

Read user input during runtime and pass the input to a container (a variable, file, etc.)

```
read INPUT
```

## Variables

### Local Variables

Local variables are those that are declared within the script and are confined to the scope they were declared inside of

```
declare LOCAL_VAR="someVal"
declare -i INT_VAR=5 # Variable that can only hold integer types, all other types are passed to the variable as 0
```

### Environment Variable

Environment variables are the variables that are loaded when the session is started and are seen by all processes spawned within this session

```
# Export a local variable as an environment variable
export ENV_VAR="globalVal"

# Print all currently loaded environment variables
printenv

# Delete a variable
unset VAR
```

## Operations

### Command Substitution

A variable can hold an entire command which can then be substituted for at any point within the script without having to re-write the same command each time

```
COMM=$(echo "some command")
echo "This is $COMM"
```

### Arithmetic Operations

```
declare -i X=10 Y=20
declare -i SUM=$(( X + Y )) # Surround all arithemtic operations with $(())
ehco $SUM
```

### Numeric Comparisons

```
if (( X > Y )) ; then
    # do something
else
    # do another thing
fi
```

### String Comparisons

```
if [[ $STR1 =~ $STR2 ]] ; then
    if [[ $STR1 !=~ $STR3 ]] ; then
        # ...
    fi
fi
```

## File & Directory Checks

- `-f`: Is it a file?
- `-d`: Is it a directory?
- `-s`: Is its size > 0 (not empty)?

```
if [[ -f "$FILE" ]] ; then
    echo "$FILE exists"
    if [[ -s "$FILE" ]] ; then
        echo "$FILE is not empty"
    else
        echo "$FILE is empty"
    fi
else
    echo "$FILE does not exist"
fi

if [[ -d "$DIR" ]] ; then
    echo "$DIR exists"
else
    echo "$DIR does not exit"
fi
```

## Outputs

- `echo`: Echoes the input string to the standard output
- `$?`: Variable that holds the exit status of a previous command. '0' means it has exited successfully, while anything else means an issue has occured
- `printf`: Same as `echo`, but it accepts string formatting in line with the C standard

## Functions

Declare a function like so

```
foo() {
    local PAR1="$1" # Pass parameters to a function exactly as you would a script
    # ...
}
```

and then call the function and pass it an argument or multiple arguments

```
foo arg1 arg2 ...
```
