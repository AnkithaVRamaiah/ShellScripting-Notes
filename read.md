### **Complete Notes on Shell Scripting**

Shell scripting is a powerful tool for automating tasks and managing systems in Unix-like environments (Linux, macOS, etc.). It allows you to write programs (scripts) that can execute a series of commands. These scripts are executed in a shell, which is a command-line interface (CLI) for interacting with the system.

Here’s a comprehensive guide to shell scripting in an understandable way:

---

### **1. What is Shell Scripting?**

- **Shell scripting** is a program written for the shell (command-line interface) to automate tasks.
- It contains a series of commands, functions, and control structures that are executed sequentially.
- A **shell** is a user interface for access to an operating system's services. The most common shells are:
  - **Bash (Bourne Again Shell)**: The default on many Linux systems.
  - **Zsh (Z Shell)**: Known for its advanced features.
  - **Tcsh**: A variant of the C shell with added features.

---

### **2. Why Use Shell Scripting?**

- **Automation**: Automates repetitive tasks like backups, log rotations, system updates, etc.
- **Efficiency**: Quickly run multiple commands in sequence without manual input.
- **Task Scheduling**: Can be scheduled using `cron` for running tasks at specified times.
- **System Management**: Automates system administration tasks like user creation, process monitoring, and file management.

---

### **3. Basic Syntax of a Shell Script**

A basic shell script typically includes:

#### **1. Shebang Line**
At the top of the script, you specify the **interpreter** that will execute the script:
```bash
#!/bin/bash
```
This line tells the system to use the `bash` shell to interpret the script.

#### **2. Commands**
Shell scripts are essentially sequences of shell commands. For example:
```bash
echo "Hello, World!"
```

#### **3. Comments**
Anything after a `#` symbol is a comment and is ignored by the shell. It’s useful for documenting the script.
```bash
# This is a comment
echo "This will print to the screen"
```

---

### **4. Variables in Shell Scripting**

Variables store data in shell scripts, such as strings, numbers, and paths.

#### **Setting Variables**
```bash
name="John"    # Assigning a string value to the variable "name"
age=25         # Assigning an integer value to the variable "age"
```

#### **Accessing Variables**
To access the value of a variable, you precede the variable with a `$`:
```bash
echo $name     # Output: John
```

#### **User Input**
You can take user input with the `read` command:
```bash
echo "Enter your name:"
read userName
echo "Hello, $userName!"
```

---

### **5. Control Structures in Shell Scripting**

Control structures allow you to make decisions and perform loops in your scripts.

#### **1. If-Else Statements**
Used for conditional execution:
```bash
if [ $age -gt 18 ]; then
  echo "You are an adult."
else
  echo "You are a minor."
fi
```

- `-gt`: Greater than
- `-lt`: Less than
- `-eq`: Equal to
- `-ne`: Not equal to

#### **2. For Loop**
Used for looping through a sequence of values:
```bash
for i in {1..5}
do
  echo "Number $i"
done
```

#### **3. While Loop**
Executes as long as a condition is true:
```bash
count=1
while [ $count -le 5 ]
do
  echo "Count is $count"
  ((count++))
done
```

---

### **6. Functions in Shell Scripting**

Functions are blocks of reusable code.

#### **Defining Functions**
```bash
function greet {
  echo "Hello, $1!"
}

greet "John"  # Output: Hello, John!
```
- `$1`: Represents the first argument passed to the function.

---

### **7. File Operations in Shell Scripting**

Shell scripts can be used to perform operations on files, such as reading, writing, and checking if files exist.

#### **1. Creating a File**
```bash
touch filename.txt    # Creates an empty file
```

#### **2. Reading from a File**
```bash
while read line
do
  echo $line
done < filename.txt
```

#### **3. Writing to a File**
```bash
echo "This is a line" > output.txt    # Overwrites the file
echo "This is another line" >> output.txt    # Appends to the file
```

#### **4. Checking if a File Exists**
```bash
if [ -f filename.txt ]; then
  echo "File exists!"
else
  echo "File does not exist!"
fi
```

---

### **8. Error Handling in Shell Scripts**

#### **Exit Status**
Every command in Linux returns an exit status:
- `0`: Command succeeded.
- Non-zero: Command failed.

You can check the exit status of the last command with `$?`:
```bash
ls /nonexistent/folder
echo $?  # Output: 2 (Error: No such file or directory)
```

#### **Using `set -e`**
To exit the script immediately if a command fails:
```bash
set -e
# If any command fails, the script will exit here
echo "This will not run if the previous command fails"
```

---

### **9. Scheduling Tasks with Cron**

You can schedule scripts to run automatically at certain times using `cron`.

#### **Editing Cron Jobs**
```bash
crontab -e
```
This opens the crontab file where you can add scheduled jobs. For example:
```
0 5 * * * /home/user/script.sh    # Runs at 5:00 AM every day
```

- `0`: Minute (0-59)
- `5`: Hour (0-23)
- `*`: Day of the month (1-31)
- `*`: Month (1-12)
- `*`: Day of the week (0-6)

---

### **10. Debugging Shell Scripts**

If your script is not working as expected, you can use the following methods for debugging:

#### **1. `-x` option**
It prints each command before executing it:
```bash
#!/bin/bash -x
echo "This will be debugged"
```

#### **2. `set -e`**
Exit immediately when a command fails.

#### **3. `echo` Statements**
Use `echo` to print the values of variables or debug specific parts of the script:
```bash
echo "The value of age is $age"
```

---

### **11. Common Shell Scripting Commands**

- `echo`: Prints text to the terminal.
- `cat`: Concatenates and displays file content.
- `grep`: Searches for text in files.
- `awk`: Processes and analyzes text.
- `sed`: Stream editor for manipulating text.
- `ps`: Displays information about running processes.
- `kill`: Terminates processes.

---

### **Example Shell Script**

Here’s an example that puts everything together:

```bash
#!/bin/bash

# Function to check disk usage
check_disk_usage() {
  echo "Checking disk usage..."
  df -h
}

# Function to backup files
backup_files() {
  echo "Backing up files..."
  tar -czf backup.tar.gz /home/user/documents
}

# Main script logic
echo "Welcome to the backup script"
echo "Choose an option:"
echo "1. Check Disk Usage"
echo "2. Backup Files"
echo "3. Exit"
read choice

case $choice in
  1) check_disk_usage ;;
  2) backup_files ;;
  3) echo "Exiting..."; exit 0 ;;
  *) echo "Invalid option!" ;;
esac
```

This script:
1. Prompts the user for input.
2. Based on the user’s choice, either checks disk usage, creates a backup, or exits.

---

### **Conclusion**

Shell scripting is a crucial skill for automating system administration tasks, managing files, and processing data. It provides flexibility and power when working in a command-line environment.

By learning **variables**, **control structures**, **functions**, **file operations**, and **scheduling**, you can significantly improve your productivity and efficiency in managing systems.

