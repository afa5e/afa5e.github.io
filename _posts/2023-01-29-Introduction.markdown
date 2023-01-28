---
layout: post
title:  "Introduction to Python at SRA"
date:   2023-01-28 16:38:41 +1100
categories: 23T1
---
Welcome to the Advanced Coding Class - Python at Sydney Robotics Academy. This 
term we will be covering a range of topics with Python:
  - I/O operations, including from the terminal and filesystem.
  - Different datatypes, such as double, float, integer, char, string, etc.
  - Different methods of storing multiple pieces of data, such as lists.
  - Making our code more readable with functions.
  - Making webpages with HTML, CSS and Javascript.

Firstly, before we can start coding, we need to install some programs. Some of 
these programs will tell our computer how to understand our code, and others 
will help us write our programs.

We will be installing all of these programs from our local website: 
<http://apps.sydneyrobotics.com.au>
1. Python 3.1x - This program will ensure that our computer can understand 
   our code. After the file has been downloaded, open the file and follow 
   the instructions.

2. Visual Studio Code. - This is a simple code editor which has some useful 
   features, including syntax highlighting. This means that our code will 
   change colours depending of what each word does, and if there are any errors.

Once these two programs have been installed, please open VSCode and you will 
see options to change the theme. You can choose any theme you want.

Now, before we write code, we first need to setup our workspace. You will need
a program called a terminal to run our code.

#### Windows
In Windows, there are two different terminals, CMD and Powershell. You can also 
install Linux through WSL2 to access a bash/zsh shell. For this lesson, we will 
be using CMD.

To open CMD, you can right click the start button, or use the keybind `WIN-X` 
to open the same menu. Then, select the `command prompt` option.

> If you do not see the `command prompt` option in the list, and instead see
> `powershell`, search for `command prompt` in windows search.
>
> Alternatively, using the run command (`WIN-R`), search for `cmd.exe`.

#### Mac OS
In Mac OS, there is only one terminal program, called Terminal. Search for this
program in the apps list and open.

### Using the Terminal

In the terminal, you should see some path to a folder. This is called the prompt
and tells you where you are in the file system. Here in the terminal, you can 
use commands to operate your computer. These commands include:

- `ls` - which lists out all files and folders in the current directory. In 
  windows, this is the `dir` command.
- `mkdir directoryName` - which makes a directory called `directoryName`.
- `cd directoryName` - changes to `directoryName`.
- `cd ..` - moves up one directory.
- `pwd` - shows the full location you are at, windows: `cd`.

Before we create any files, we should first change to our desktop folder and
create a new folder for this term. You folder name must not contain any special 
characters or spaces. If you are continuing from last term, or the holiday you 
can move the folder from that previous class into this new folder under a name 
such as `22T4` or `RoverRun`. 

<details>
    <summary>Hint:</summary>
    <br>
    <ol>
        <li><code>ls</code> or <code>cd</code> to print the contents of the 
        current directory.</li>
        <li>Then, <code>cd</code> into the Desktop folder.</li>
        <li>Now, make a new folder with <code>mkdir</code> with an appropriate 
        name.</li>
        <li>Finally, <code>cd</code> into the newly created folder.</li>
    </ol>
</details>
<br />

Finally, we need to check which command we use to run our python files. To do 
this, try these commands:

- Windows: `py --version`
- Mac OS: `python --version`

If the command returns a version number starting with 2, you will need to use 
these commands:

- Windows: `py -3 --version`
- Mac OS: `python3 --version`

Now, during the term, when you are running your code, you will need to remember 
which command prefix to use.

### Using VSCode

Now that you have finished setting up VSCode and the terminal, we can use the 
keyboard shortcut `CTRL/CMD-N` to create a new file, then we can save the new 
file with `CTRL/CMD-S`, naming it with the `.py` extension. This tells your 
computer thatthe file is a python file, allowing VSCode to apply syntax 
highlighting.

You should now see a view that looks like this:

![VSCode](/img/vscode.png)

