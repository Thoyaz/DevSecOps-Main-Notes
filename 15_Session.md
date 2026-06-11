# Shell Scripting Notes

---

# Shebang

```bash
#!/bin/bash
```

==> it is a shibang, It is the first line in the shell script, that reprasents the path of interpretter, What ever you write in side the shell script that will be executed by this shebang

---

# Echo Command

```bash
echo "Hello TZ"
```

==> This is to print the text in terminal

---

# Variables

Variables follow DRY → Do Not Repeat Yourself

* Change in one place reflect everywhere you refer
* Easy to maintain
* Readable

### Example:

#### Declaring variable:

```bash
$VARIABLE_NAME=<value>
```

#no space between variable and the value

#### Use the variable:

```bash
echo “My name is ${VARIABLE_NAME}”
```

---

# Example of shell Script where we use variables

```bash
#!/bin/bash

PERSON1=Trump # no space between value and =
PERSON2=Putin

echo "$PERSON1:: Hello $PERSON2, How are you?"
echo "$PERSON2:: Hi $PERSON1, I am fine thanks for asking. How are you doing?"
echo "$PERSON1:: doing fine. What are you learning $PERSON2?"
echo "$PERSON2:: I am learning Shell. What about you?"
```

---

# How to pass values while running the shell script?

### Example of running script :

```bash
sh hello.sh tz pc
```

### Example script:

```bash
#!/bin/bash

PERSON1=$1 # no space between value and =
PERSON2=$2

echo "$PERSON1:: Hello $PERSON2, How are you?"
echo "$PERSON2:: Hi $PERSON1, I am fine thanks for asking. How are you doing?"
echo "$PERSON1:: doing fine. What are you learning $PERSON2?"
echo "$PERSON2:: I am learning Shell. What about you?"
```

---

# How to pass a password in hidden format?

```bash
#!/bin/bash

echo "Please Enter your username::"
read USER_NAME 	# Terminal will ask user to enter input

echo "User name is $USER_NAME"

echo "Please enter your password::"
read -s PASSWORD		# Terminal will ask user to enter input

echo "Password is $PASSWORD"
```

---

# I want a command to be executed and take the output into variable, how to do that?

```bash
VAR_NAME=$(command)
```

### Example script

```bash
#!/bin/bash

START_TIME=$(date +%s)		# Prints the time in sec (+%s)

echo "Script executed at: $START_TIME"

sleep 10

END_TIME=$(date +%s)
TOTAL_TIME=$(($END_TIME-$START_TIME))

echo "Script executed in: $TOTAL_TIME seconds"
```

---

# Special variables

### Arguments passed to script

```text
$1 $2 ... $N args passed to script
```

### All variables passed to script

```text
$@
```

### Number of variables passed to script

```text
$#
```

### Script name

```text
$0
```

### Present which directory you are in

```text
$PWD
```

### Who is running this script

```text
$USER
```

### Home direcory of the user

```text
$Home
```

### PID of the script

```text
$$
```

### Background process id

```bash
sleep 100 &
```

```text
$!
```

### Exit status of previous command

```text
$?
```

---

# $@ vs $*

### $@

treats args seperately

### $*

treats as single args

---

# Example Script

```bash
#!/bin/bash

#### Special Variables ####
echo "All args passed to script: $@"
echo "Number of vars passed to script: $#"
echo "Script name: $0"
echo "Present directory: $PWD"
echo "Who is running: $USER"
echo "Home directory of current user: $HOME"
echo "PID of this script: $$"
sleep 100 &
echo "PID of recently executed background process: $!"
echo "All args passed to script: $*"
```

---

# Data Types

variables are holding data..

### mobile number -> numbers

* integers -> -33,768 -> 33,768
* float -> 45.90
* decimanl -> long number
* complex -> 4+8i

### names -> string

### major? -> yes or no boolean

### skills -> devops aws docker kubernetes -> list of skills

### skills -> map or dictionary

```text
devops: 4 -> key -> value
docker: 3
kubernetes: 2
```

```text
areane4 -> 5

speed round up -> 8.2km/sec -> 8km/sec

copied code
```

```text
integer speed=8km/sec

integer speed=8.2km/sec

number

string
```

### Important

everything is string in shell

position/index in coding starts from 0

---

# Example script

```bash
#!/bin/bash

NUM1=100
NUM2=sivakumar

SUM=$(($NUM1+$NUM2))

echo "Sum is: $SUM"

# Array
FRUITS=("Apple" "Banana" "Pomo")

echo "Fruits are: ${FRUITS[@]}"
echo "First Fruit is: ${FRUITS[0]}"
echo "Second Fruit is: ${FRUITS[1]}"
echo "Third Fruit is: ${FRUITS[2]}"
```

---

# Conditions

conditions

if or when

### Syntax 1

```bash
if [ expression ]; then
	code here
fi
```

### Syntax 2

```bash
if [ expression ]; then
	code here
elif [ expression ]; then
	code here
else
	code here
fi
```

---

# Example script

conditions

if or when

### Syntax 1

```bash
if [ expression ]; then
	code here
fi
```

### Syntax 2

```bash
if [ expression ]; then
	code here
elif [ expression ]; then
	code here
else
	code here
fi
```

---

# EXIT code

```text
0-127
```

### Success

```text
0 -> success
```

### Failure

```text
anything else -> failure
```

### Example

```text
nginx

dnf install nginx -y

if root user then success

otherwise failure

root user id -> 0

other users -> greater than 0
```

---

# Example script

```bash
#!/bin/bash

USERID=$(id -u)

if [ $USERID -ne 0 ]; then
    echo "Please run this script with root user access"
    exit 1
fi

echo "Installing Nginx"
dnf install nginx -y

if [ $? -ne 0 ]; then
    echo "Installing Nginx ... FAILURE"
    exit 1
else
    echo "Installing Nginx ... SUCCESS"
fi

dnf install mysql -y

if [ $? -ne 0 ]; then
    echo "Installing MySQL ... FAILURE"
    exit 1
else
    echo "Installing MySQL ... SUCCESS"
fi

dnf install nodejs -y

if [ $? -ne 0 ]; then
    echo "Installing nodejs ... FAILURE"
    exit 1
else
    echo "Installing nodejs ... SUCCESS"
fi
```
