---
layout: default
---

Hey there, let's learn how to use the command line!

## Schedule

0. [Let's learn a few things about each other](#yo)
0. [So, why bother to learn the command line?](#why)
0. [What is the command line and how do I get there?](#what)
0. [Wait, where am I? Who am I?](#where-who)
0. [Moving around on the command line](#moving-around)
0. [File management](#file-management)
    0. Make things like files and folders
    0. Move things around or copy them
    0. Remove things, *carefully*
0. [Wait, how am I supposed to remember all this?](#remember)
0. [Some basic HTTP](#http)
0. [A few handy tools](#tools)
    0. `cat` and `grep`
    0. `curl`
    0. `apt-get` or `brew`
    0. `git`
0. [Control flow](#control)
0. [Tricks you might want to know](#tricks)

<a name="yo"></a>

## Yo, my name is Jeremia

If you have any questions after this class, you can always get in touch with me on Twitter. My handle is [@jeremiak](https://twitter.com/jeremiak).

What's your name and what are you interested in learning today?

<a name="why"></a>

## Why?

Power, flexibility, repeatability. The command line is a rich universe of tools and practices that help you manage your computer in a convenient and repeatable way: aka scripting. Anything you do on the command line can be scripted, and you can do a lot from the command line.

When you feel familiar and comfortable on the command line the tools that are available to you will become much more numerous.

<a name="what"></a>

## What is the command line and how do I get there?

### Mac and Linux

Many times the command line interface is in an application called "terminal". On a Mac, you should be able to find the Terminal.app in `/Applications/Utilities/`. This is how we describe locations on the command line. The initial `/` signifies the "root", the top most part of the harddrive. On your desktop, this is represented by your "Macintosh HD". Each `/` means folder. So we can read this location as the "Utilities" folder inside of the "Applications" folder, which is inside the root folder (the harddrive).

On a Linux machine, you should easily be able to find a "Terminal" application from one of the main menus. Linux and Mac OS X are very similar because they are both based on another operating system called Unix. There are some small differences, however, but only one that we need to worry about initially: case sensitivity. On a Mac machine the command line treats "/AppliCATIONs" and "/Applications" and "/applications" as the same thing. Linux treats them as different things. Proceed with caution.

Open up your command line interface once you find it. You'll know you are in the right place if you see some monospace text.

### Windows

I'm going to be honest with you, I know very little about Windows shell environments. I've never really used one though some of my friends who develop on Windows machines use something called [PowerShell](#). The Windows and Linux/Mac command line environments are similar in their appearance but are about as different as the graphical user interfaces. Many development boxes are based on Linux, and so most command line tools are written for the Linux/Mac environments. For the purposes of today, I'd like for you to get a free, virtual shell at [c9](https://c9.io)

<a name="where-who"></a>

## Wait, where am I? Who am I?

Let's get our bearings. We're in this new world of monospace fonts and a seemingly out of place `$` sign. We're in the computer. Think of this as an old school Finder, if you're on a Mac. Its much rougher around the edges but once you start to feel comfortable here you'll be able to greatly increase your own productivity. But where in the computer are we? There's a simple command to ask the computer to print out our current location, sometimes called the "working directory": `pwd` (print working directory).

To run a command on the command line, simply type the command press return. Let's try it. Go ahead and type `pwd` followed by the enter/return key. When I do that, I see something like `/Users/JeremiaKimelman`. I can read this as I am in the "JeremiaKimelman" folder inside of the "Users" folder, which itself resides in the root of the computer. That makes it sound like there is a user on the system named "JeremiaKimelman". I wonder if that's me...

We can get our current username by asking `whoami`? This command is pretty easy to remember, go ahead and try `whoami` followed by the return key. Somewhat predictably, when I run the command I get "JeremiaKimelman" as the result.

Great, so we know who we are and where we are. That's a solid start.

<a name="moving-around"></a>

## Moving around on the command line

Now that we know where we are, let's take a look around and go exploring. We use the `ls` (list) command to see what is in a folder. What's in the folder we're currently in? On the command line there are a few special characters that have meanings. Two of them are:

0. `.`
0. `..`

The single period means the current directory, the folder you are in when the command is executed. Two dots means our parent folder. That is to say the folder that contains the folder we're currently in. Since I'm still in `/Users/JeremiaKimelman`, `.` would be equivalent to my current folder ("JeremiaKimelman") and `..` would represent the `/Users` folder.

Let's use the `ls` command and see what else is in our current folder. With `ls .` we instruct the computer to tell us what other things we're looking at.

Think of the `.` in the above example as a parameter that you are giving to the `ls` program. You're giving the `ls` program a file path (like the address of a file) and it will return to you the listings of the folder at the end of the file path. That means that we can look at any folder in the computer from almost any other (ignoring things like security permissions for the moment). So let's use a few other file paths we already know about see if we can learn more about what's on this computer. We're already familiar with `..` so let's try that! The double dots means the parent directory so when we run `ls ..` we're asking for the listing of the contents of the folder containing the folder we're currently in.

We also know that `/` represents the very root of the file system. Let's try and see what is in the harddrive of the computer with `ls /`.

Now, let's get the heck out of dodge already, we've been in this directory for a while and its kind of boring. We can change our current directory to any other by passing a path to the `cd` (change directory). For example, if we want to change to our parent directory we can `cd ..`, if we want to go to the root of the disk we can `cd /`. There's another special symbol that's pretty common, which is the `~`. In this command line context the `~` refers the current user's home directory. This is where we likely started out to begin with. In any case, it is helpful to know that you can `cd ~` from anywhere on your computer and get to your home directory.

Use `ls` and `cd` to try and navigate around for a few minutes. It is uncomfortable now and might feel like arcane kind of syntax but it is just a matter of getting familiar with it. Soon you'll be zipping around your machine like it is second nature.

<a name="file-management"></a>

## File management

### Making things

Moving around folders that are already created are good and all, but let's make some of our own. We can make either files or folders, which is pretty helpful because almost everything on your computer can be thought of as either a file or a folder. A folder holds files, and files generally hold words.

Let's return to our home directory (`cd ~`) and make a folder called "yum". Remember, folders are also called directories so the command we want is `mkdir` (make directory). In this case `mkdir yum` will do the trick. Confirm that the directory has been created with `ls`.

Let's go into this new folder we've created and make a few files, we'll call them "cake", "cookies", and "pineapples". The command to make files is called `touch`. So we `touch cake`, `touch cookies`, and `touch pineapples` - sounds like a good day if you ask me. Use `ls` to confirm that we did everything correctly.

### Moving and copying things

Let's say that we're actually going through a period of not eating butter so we want to put those files somewhere else, to move them from "yum" to "yuck". First, let's go to our home directory. Then make a folder called "yuck". We can move files with the `mv` (move) command. It works like all the other commands we've used so far and takes a file path. Actually, it takes two file paths, one "source" path and one "destination" path. Basically from where and to where we want the file to move. Let's move our "cake" file from the "yum" folder to the "yuck" one. We do that with `mv yum/cake yuck/`. Go ahead and move the "cookies" file over.

If you take a look inside your "yum" folder, you'll notice that it only has one file still in it. So moving takes a file from one place and puts it in another. Sometimes, that's too extreme and we want the file to be in both places. We can copy files with the `cp` (copy) command. Let's copy both of the files back to our "yum" folder.

Starting with the "cake" file, we can copy it over with `cp yuck/cake yum/cake`. Go ahead and move our cookie file over as well.

### Get rid of things

Can we all agree that cake, cookies and pineapples are all decidely on the yum side of the spectrum. So let's just get rid of the "yuck" folder all together. We can delete files or folders with `rm` (remove). So let's give it a try:

`rm yuck`

Why didn't that work? The error is that telling us that "yuck" is a directory and therefore it refuses to cooperate. This is when we learn about a concept in this command line called "flags". Flags are configuration options that you can pass to commands that change how it behaves. Generally speaking they come between the command and the file path and start with `-` or `--`. In this case, the `rm` command accepts a `-r` flag that makes it work with directories. Let's try it again, like `rm -r yuck`. Confirm that it worked using `ls`.

Now, let's look at a few commands and you tell me what they'll do:

- `rm resume.pdf`
- `rm -r ./`
- `rm -r /`

Notice the very subtle, but very important difference between those last two. One is very benign and one is very not. The takeaway is that small differences can have huge consequences on the command line. That whole thing about with great power...

<a name="remember"></a>

## Wait, how am I supposed to remember all this?

You're not.

I look up documentation and syntax all the time. All. The. Time. There's a couple of helpful sources of information on the command line. The first thing you generally want to use is `man` (manual). You use `man` by passing it the name of the command you need help with. For instance, if we forgot what flag to pass the `rm` command to remove folders, `man rm` would be able to help us out.

Use `man` to figure out what flag we pass to `ls` so that a slash is added after files that are directories.

Another common, though not ubiquitous, way to get help is to use the `--help` flag with a command. For example, if you already have `git` installed you can use `git --help` to learn more about how to use it.

<a name="http"></a>

## Some basic HTTP


<a name="tools"></a>

## A few handy tools


<a name="control"></a>

## Control flow

- `&` and `&&`
- `>`

<a name="tricks"></a>

## Tricks you might want to know

Sometimes you just have to quit. I mean, everybody knows force quit on Mac and Control-Alt-Delete on Windows. In this environment, the command to totally stop is Control-C.

And sometimes you end up in this text editor called `vi`. It is actually insanely useful and ergonomic but has a sharp learning curve. I've found that its helpful to know that `:q` is the quit command for `vi`.

There are also some handy keyboard shortcuts to make you a bit more productive. Here are some of the most helpful ones:

- Control-U clears the line from the cursor point back to the beginning
- Control-A moves the cursor to the beginning of the line
- Control-E moves the cursor to the end of the line
- Control-R allows you to search through the previous commands

## Keep on learning

Here are some great resources to help you get more comfortable with the command line.

- [The Command Line Crash Course](http://cli.learncodethehardway.org/book/)
