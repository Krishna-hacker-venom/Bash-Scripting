Bash (Bourne Again SHell): An improved version of sh, with additional features like command history and tab completion.
What is Bash?
Bash is used to run commands and write scripts on Unix/Linux systems.
---
Bash is the default shell on most Linux and macOS systems."Shell" is a general category, while "Bash" is a specific product within that category. Think of "Shell" as the general concept of a motor vehicle, and "Bash" as a specific model of car, like a Ford Mustang.
---
Practical Uses of Bash
System administrators use Bash to:
    Automate tasks
    System operations
    Process data
Developers use Bash for:
    Build automation
    Testing
    Deployment
    Data processing and manipulation
---
cd ..: Move up one directory level
cd ~: Change to the home directory
cd -: Switch to the previous directory
cd /: Change to the root directory
---
The pwd command supports a few options to customize its output:

    -L: Display the logical current working directory
    -P: Display the physical current working directory (without symbolic links)
---
The echo command has several options to customize its output:

    -n - Don't add a new line at the end
    -e - Allow special characters like \n for new lines
    -E - Don't allow special characters (default)
---
-b for non-blank line
e.g cat -b <file_name>
-s option removes extra empty lines from the output, leaving only a single blank line where multiple ones existed
--
Concatenate Two Files

The cat command can be used to concatenate multiple files into one.

This is useful for combining files or appending content to an existing file.
--cat with Piping

The cat command is often used with piping to send the content of files to other commands.

This is useful for processing text data.
---

