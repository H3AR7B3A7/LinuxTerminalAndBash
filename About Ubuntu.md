# About Ubuntu

Ubuntu is a Linux distribution based on Debian and composed mostly of free and open-source software.
Ubuntu is officially released in three editions: Desktop, Server, and Core for Internet of things devices and robots.
All the editions can run on the computer alone, or in a virtual machine. Ubuntu is a popular operating system
for cloud computing, with support for OpenStack. Ubuntu's default desktop has been GNOME, since version 17.10.


## Unix Philosophy

Unix is a family of multitasking, multiuser computer operating systems that derive from the original AT&T Unix,
whose development started in the 1970s at the Bell Labs research center by Ken Thompson, Dennis Ritchie, and others.

Unix systems are characterized by a modular design that is sometimes called the "Unix philosophy".
According to this philosophy, the operating system should provide a set of simple tools, each of which performs
a limited, well-defined function. A unified filesystem (the Unix filesystem) and an inter-process communication
mechanism known as "pipes" serve as the main means of communication, and a shell scripting and command language
(the Unix shell) is used to combine the tools to perform complex workflows.

Debian and consequently Ubuntu are often called Unix-like OS because they share the same Unix philosophy.


## Advanced Packaging Tool

A free-software user interface that works with core libraries to handle the installation and removal of software on
Debian, Ubuntu, and related Linux distributions.
APT simplifies the process of managing software on Unix-like computer systems by automating the retrieval,
configuration and installation of software packages, either from precompiled files or by compiling source code.


## Ubuntu Server

Like other distributions, Ubuntu comes in two editions:
- Desktop
- Server

The server edition has no GUI, instead it only uses the shell.
It is a lean (1 GB of disc space) efficient operating system, ideally only rarely requiring updates.
It has the same release schedule, but only LTS releases should be considered for server stability.

The installation differs significantly from the desktop version. However, it offers a lot of build in functionality,
like security and different software (to set up: webserver, mail server, files server, ...).

OpenSSH allows for controlling the server securely from a different machine.


## Linux Terminal

Way back when, computers were huge multi-user systems owned by universities and corporations.
The machine itself was located in a secure room that ordinary users didn't visit.
Instead, they interacted with it via a terminal. In the early days,
the terminal would have been a printer (a teletype, hence TTY). Input was via punch cards and output via a printer.
Later, a terminal was a display with a keyboard.

Today’s terminals are software representations of the old physical terminals, often running on a GUI.
It provides an interface into which users can type commands and that can print text.
When you SSH into your Linux server, the program that you run on your local computer and type commands into is a terminal.


## Linux Console

Originally, a console was a terminal “plugged into” the computer: it provided the interface that was used to configure
and control the computer and to view messages from the operating system.

When a Linux server first boots, it prints status messages to the console, the familiar scroll of text that brings joy
to many a Linux user. When you interact with your server, you connect a terminal to a program running in a console.


## Linux Shell

The broadest definition of a shell is a program that runs other programs, but when you hear shell in the Linux world,
it almost certainly refers to a command line shell — the program that creates and manages the command line interface
into which users type commands.

For example, when you type “ls” into a terminal connected by SSH to your Linux server,
you are asking the shell to run the “ls” program and to print out a list of files in the current directory to your terminal.
The shell also provides a programming language of sorts, shell script, that can be used to tie together multiple commands.

The most common shell is Bash, the Bourne Again Shell, but there are several variants; Ubuntu uses the Dash shell,
and some Linux users prefer the Fish or ZSH shells.

