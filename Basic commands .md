# Bash Notes

## What is Bash?

**Bash** stands for **Bourne Again SHell**. It is an improved version of the original Unix shell (`sh`) and provides features such as:

* Command history
* Tab completion
* Variables
* Functions
* Scripting
* Command substitution
* Job control

Bash is commonly used to run commands and write shell scripts on Unix/Linux systems.

> **Shell vs Bash**
>
> **Shell** is a general category of command-line interpreters, while **Bash** is a specific shell implementation.
>
> Think of **Shell** as the general concept of a car, while **Bash** is a specific model.

---

## Practical Uses of Bash

### System Administrators

Bash is commonly used for:

* Automating repetitive tasks
* System administration
* File and directory management
* Process management
* System operations
* Log processing
* Backup automation

### Developers

Developers use Bash for:

* Build automation
* Testing
* Deployment
* CI/CD automation
* Data processing
* File manipulation
* Running development tools

---

# Basic Navigation Commands

## `cd`

The `cd` command is used to change the current working directory.

```bash
cd directory_name
```

### Useful `cd` Commands

| Command           | Description                             |
| ----------------- | --------------------------------------- |
| `cd ..`           | Move up one directory level             |
| `cd ~`            | Go to the current user's home directory |
| `cd -`            | Switch to the previous directory        |
| `cd /`            | Go to the root directory                |
| `cd /path/to/dir` | Go to a specific directory              |

Example:

```bash
cd /var/log
```

---

# `pwd`

`pwd` stands for **Print Working Directory**.

It displays the current directory.

```bash
pwd
```

### Options

| Option | Description                                                           |
| ------ | --------------------------------------------------------------------- |
| `-L`   | Display the logical current working directory                         |
| `-P`   | Display the physical current working directory without symbolic links |

Examples:

```bash
pwd -L
pwd -P
```

---

# `echo`

The `echo` command prints text or variable values to the terminal.

```bash
echo "Hello World"
```

### Options

| Option | Description                                                                      |
| ------ | -------------------------------------------------------------------------------- |
| `-n`   | Do not print a newline at the end                                                |
| `-e`   | Enable interpretation of escape sequences                                        |
| `-E`   | Disable interpretation of escape sequences; default in many Bash implementations |

Example:

```bash
echo -e "Hello\nWorld"
```

Output:

```text
Hello
World
```

---

# `cat`

`cat` is short for **concatenate**.

It is commonly used to:

* Display file contents
* Concatenate files
* Create files
* Send file contents to other commands using pipes

### Display a File

```bash
cat filename.txt
```

### `cat -b`

Number non-blank lines.

```bash
cat -b filename.txt
```

### `cat -s`

Suppress repeated empty lines.

```bash
cat -s filename.txt
```

Multiple consecutive blank lines are reduced to a single blank line.

---

## Concatenate Two Files

You can combine multiple files using `cat`.

```bash
cat file1.txt file2.txt
```

To save the combined output:

```bash
cat file1.txt file2.txt > combined.txt
```

---

## `cat` with Piping

The output of `cat` can be sent to another command using a pipe (`|`).

```bash
cat access.log | grep "404"
```

This sends the contents of `access.log` to `grep`, which searches for lines containing `404`.

> In many cases, `grep "404" access.log` is simpler, but piping is useful for understanding Bash command chaining.

---

# `cp`

The `cp` command is used to **copy files and directories**.

### Syntax

```bash
cp source destination
```

Example:

```bash
cp file.txt backup.txt
```

### Common Options

| Option | Description                                                                       |
| ------ | --------------------------------------------------------------------------------- |
| `-r`   | Recursively copy directories and their contents                                   |
| `-i`   | Ask before overwriting an existing file                                           |
| `-u`   | Copy only when the source is newer than the destination or destination is missing |
| `-v`   | Verbose mode; show files being copied                                             |

Examples:

```bash
cp -r project/ backup/
```

```bash
cp -i file.txt backup.txt
```

```bash
cp -v file.txt /tmp/
```

---

# `mv`

The `mv` command is used to **move or rename files and directories**.

### Rename a File

```bash
mv old_name new_name
```

Example:

```bash
mv test.txt notes.txt
```

### Move a File

```bash
mv file.txt /tmp/
```

### Common Options

| Option | Description                                                  |
| ------ | ------------------------------------------------------------ |
| `-i`   | Ask before overwriting                                       |
| `-u`   | Move only when the source is newer or destination is missing |
| `-v`   | Verbose mode; show files being moved                         |

---

## `mv` with Wildcards

Wildcards can be used to work with multiple files.

For example:

```bash
mv *.txt /destination/
```

This moves all files ending in `.txt` into the destination directory.

### Common Wildcards

| Wildcard | Meaning                                    |
| -------- | ------------------------------------------ |
| `*`      | Matches zero or more characters            |
| `?`      | Matches exactly one character              |
| `[]`     | Matches one character from a specified set |

Example:

```bash
ls *.log
```

---

# `rm`

The `rm` command is used to **remove files and directories**.

### Remove a File

```bash
rm filename
```

### Common Options

| Option | Description                                       |
| ------ | ------------------------------------------------- |
| `-r`   | Recursively remove directories and their contents |
| `-i`   | Ask for confirmation before deleting              |
| `-f`   | Force deletion without confirmation               |
| `-v`   | Verbose mode; show files being removed            |

Examples:

```bash
rm file.txt
```

```bash
rm -r directory/
```

```bash
rm -i important.txt
```

> **Warning:** `rm` normally does not move files to a recycle bin. Deleted files may be difficult or impossible to recover.

Be especially careful with:

```bash
rm -rf
```

---

# `touch`

The `touch` command is commonly used to:

* Create an empty file if it does not exist
* Update file access/modification timestamps

### Create a File

```bash
touch filename.txt
```

If the file does not exist, an empty file is created.

If it already exists, its timestamps are updated.

### Common Options

| Option | Description                               |
| ------ | ----------------------------------------- |
| `-a`   | Change only the access time               |
| `-m`   | Change only the modification time         |
| `-t`   | Set the timestamp using a specified time  |
| `-c`   | Do not create a file if it does not exist |

Examples:

```bash
touch notes.txt
```

```bash
touch -a file.txt
```

```bash
touch -m file.txt
```

```bash
touch -c file.txt
```

---

# `mkdir`

The `mkdir` command is used to **create directories**.

### Syntax

```bash
mkdir directory_name
```

Example:

```bash
mkdir projects
```

### Common Options

| Option | Description                                  |
| ------ | -------------------------------------------- |
| `-p`   | Create parent directories as required        |
| `-v`   | Display a message for each created directory |
| `-m`   | Set the directory permissions                |

### Create Nested Directories

Without `-p`:

```bash
mkdir project/src
```

This requires the `project` directory to already exist.

With `-p`:

```bash
mkdir -p project/src
```

Bash creates the required parent directories automatically.

---

# `man`

The `man` command displays the **manual page** for a command.

### Syntax

```bash
man <command>
```

Example:

```bash
man ls
```

```bash
man cp
```

```bash
man bash
```

### Useful Keys Inside `man`

| Key     | Action                      |
| ------- | --------------------------- |
| `Space` | Move down one page          |
| `b`     | Move up one page            |
| `/word` | Search for a word           |
| `n`     | Find the next search result |
| `q`     | Quit                        |

---

# Bash Aliases

An **alias** allows you to create a short name for a frequently used command.

### Syntax

```bash
alias name='command'
```

Example:

```bash
alias ll='ls -la'
```

Now you can use:

```bash
ll
```

instead of:

```bash
ls -la
```

### View Existing Aliases

```bash
alias
```

### Remove an Alias

```bash
unalias ll
```

---

# Permanent Bash Aliases

Aliases created using `alias` normally exist only for the current shell session.

To make an alias permanent, add it to your Bash configuration file.

On many Linux systems:

```bash
~/.bashrc
```

Example:

```bash
alias ll='ls -la'
alias cls='clear'
alias update='sudo apt update'
```

After editing `~/.bashrc`, reload it:

```bash
source ~/.bashrc
```

The aliases will then be available in new Bash sessions.

> **Note:** `~/.bash_profile` or `~/.profile` may also be used depending on how the shell/session is configured. On many Linux distributions, `~/.bashrc` is the usual place for interactive Bash aliases.

---

# Quick Command Cheat Sheet

| Command | Purpose                          |
| ------- | -------------------------------- |
| `cd`    | Change directory                 |
| `pwd`   | Show current directory           |
| `echo`  | Print text/output                |
| `cat`   | Display or concatenate files     |
| `cp`    | Copy files/directories           |
| `mv`    | Move or rename files/directories |
| `rm`    | Remove files/directories         |
| `touch` | Create files/update timestamps   |
| `mkdir` | Create directories               |
| `man`   | Display command documentation    |
| `alias` | Create/view command aliases      |

---

# Basic Bash Workflow

A simple Bash workflow might look like this:

```bash
pwd
mkdir project
cd project
touch notes.txt
echo "Bash Notes" > notes.txt
cat notes.txt
cp notes.txt backup.txt
mv backup.txt backup_notes.txt
ls -la
```

This demonstrates basic:

```text
Check location
     ↓
Create directory
     ↓
Enter directory
     ↓
Create file
     ↓
Write content
     ↓
Read content
     ↓
Copy file
     ↓
Rename file
     ↓
List files
```

---

# Bash for Cybersecurity

Bash is especially useful in cybersecurity because many security tools and Linux systems are operated through the command line.

Common uses include:

* Log analysis
* File searching
* Process investigation
* Network troubleshooting
* Automation
* Security tool automation
* CTF workflows
* System administration
* Incident-response tasks
* Parsing command output

Example:

```bash
grep "Failed password" /var/log/auth.log
```

This can be useful for finding failed SSH authentication attempts in systems where that log file is used.

Another example:

```bash
ps aux | grep ssh
```

This can help identify processes related to SSH.

---

# Key Bash Concepts to Learn Next

After learning these basic commands, continue with:

1. **File permissions**

   * `chmod`
   * `chown`
   * `chgrp`

2. **Process management**

   * `ps`
   * `top`
   * `kill`
   * `jobs`
   * `bg`
   * `fg`

3. **Text processing**

   * `grep`
   * `awk`
   * `sed`
   * `cut`
   * `sort`
   * `uniq`

4. **Redirection and pipes**

   * `>`
   * `>>`
   * `<`
   * `|`
   * `2>`
   * `&>`

5. **Bash scripting**

   * Variables
   * `if/else`
   * Loops
   * Functions
   * Arguments
   * Exit codes

6. **Networking commands**

   * `ip`
   * `ss`
   * `curl`
   * `wget`
   * `ping`
   * `dig`

7. **Security-focused commands**

   * `find`
   * `grep`
   * `strings`
   * `file`
   * `chmod`
   * `sudo`
   * `ssh`
