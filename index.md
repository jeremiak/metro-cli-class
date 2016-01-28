---
layout: default
published: true
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
0. [Control flow](#control)
0. [A few handy tools](#tools)
    0. `cat` and `grep`
    0. `apt-get` or `brew`
    0. `git`
    0. `curl`
0. [Some basic HTTP](#http)
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

<a name="control"></a>

## Control flow

One really great thing about the command line is that you get to control the flow of data between commands and files at a pretty granular level. In technical parlance, this is called streaming but I think its easiest to think about flow.

First let's learn about chaining commands together. For example, what if you wanted to go to the root directory and then list all of the files there with a single command? We can join commands together with the `&` character. Sometimes we'll see it as a single `&` and other times it will be `&&`. These mean pretty different things.

The double ampersand means that you want the commands to be executed in sequential order, with a given command only being executed after the one before it has finished. In this case we can easily chain our `cd` and `ls` commands like such: `cd / && ls -al .`

We use the single ampersand when we want the task to be moved to the background immediately and the next command to be issued. This one is a bit more advanced than the double ampersand so I'd stick with `&&` for now.

The flow of data is also under our control using the `>` operator. It kind of looks like exactly what it does. It takes a stream of data and puts it somewhere else, generally a file. So let's say you wanted to list the contents of your home directory in a file to send to tech support, we could something like this: `ls ~ > ~/listing.txt`

Use `man`, `ls`, and the `>` to generate a file called `stuff.txt` in your home directory.

We can also pipe data from one command to the next so that the output of one command forms the basis for the input of another with the `|` operator. This can be pretty helpful, but I'm going to give you one good example that will immediately be useful. If we pipe the output to the `less` command it will give us a nice interface through which to read very, very long data streams.

For example, let's say we wanted to slowly page through the entire listing of the computer. We can use `ls -R / | more` so that we can slowly read the file using the arrow keys (or `vi` shortcuts if that's your thing). To get out of that view, just press `q`.

To recap:

- `&&` - chain commands together, a command will be executed when the one before it has finished
- `&` - run a command in the background and return/finish immediately
- `>` - output to a file
- `|` - pipe commands together

<a name="tools"></a>

## A few handy tools

### `cat` and `grep`

These are some pretty helpful, standard tools for interrogating textual data. `cat` (catenate, even though that really doesn't help in this case) shows us the data that is inside of a file. Let's take a look at that `stuff.txt` file we created just a minute ago. Since its in our home directory, we should be able to see it with `cat ~/stuff.txt`. What do you see when you do that? Remember, with long text files like this we probably want to use `| more` so that hundreds of lines of text don't immediately get printed to the screen.

We learned that we can use the `|` and `more` to read through text but what if we're just looking for something in particular? Computers are really good at searching large bodies of text, way better than humans are. So let's put our computers to work.

We'll be using the `grep` (globally search a regular expression and print) command along with the pipe operator. For example, let's say we want to see if there's a file named `stuff.txt` and one named `nowhere.txt` in our home directory.

First, we can list all the contents of our home directory and then pipe that to the grep command with a string to search with. You can actually use regular expressions here, but that's a topic worthy of a whole other class. To be honest, I've been programming computers for years and I still have to read regular expression documentation.

What does `ls ~ | grep stuff.txt` output? What does `ls ~ | grep nowhere.txt` output? Why do you think they're different and what does it mean? What commands could we have used instead of `ls ~` in this case?

Now that we're all done with the `stuff.txt`, let's make sure to remove it since it contains an itemized listing of all of the contents of your home directory.

### Install new tools with `apt-get` or `brew`

In this command line environment we also have something very akin to an app store. We call them repositories, generally, and it will vary from operating system to operating system. On Mac, the best tool to use is [`brew`](http://brew.sh/) which you'll have to install yourself.

On lots of Linux distributions you should be able to immediately use `apt-get`. Go ahead and run `apt-get` to see if the command is installed. In general, if you want to see if a command is installed you can try and run it or you can use `which <command>`. In this case, `which apt-get`.

We're not going to install anything with these tools but they provide a clear and repeatable way to get your system set up. They also remove lots of the pain dealing with "dependency management", which is the commands that a particular command relies on.

<a name="http"></a>

## Some basic HTTP

HTTP (hypertext transfer protocol) is one of the major transport mechanisms for data on the web. It is what browers use (that's why there's that weird `http://` or `https://` in the URLs you visit) to get webpages from remote servers. The very basics of HTTP are that you need a URL to request and you can use an "HTTP verb" to indiciate the type of request. There are four major HTTP verbs that we use on the web:

0. `GET` for getting (reading) information
0. `POST` for creating information on the server
0. `PUT` for updating information on the server
0. `DELETE` for (surprise!) deleting information on the server

Generally speaking, your browser makes `GET` requests to which the server generally returns HTML or JSON. `GET` is sort of the default method when talking about HTTP, but comes the limitiation that data isn't generally created on the server in response.

On your command line you can use the `curl` command to make HTTP requests, which will be `GET` by default.

For example, go ahead and try `curl example.com`. What happens?

Using our control flow knowledge, we can just scrape that web page super easily! Let's put the HTML from our `curl` command above into a page called `example.html`.

How can we do this? `curl example.com > example.html` should work great.

<a name="tricks"></a>

## Tricks you might want to know

Sometimes you just have to quit. I mean, everybody knows force quit on Mac and Control-Alt-Delete on Windows. In this environment, the command to totally stop is Control-C.

And sometimes you end up in this text editor called `vi`. It is actually insanely useful and ergonomic but has a sharp learning curve. I've found that its helpful to know that `:q` is the quit command for `vi`.

There are also some handy keyboard shortcuts to make you a bit more productive. Here are some of the most helpful ones:

- Control-U clears the line from the cursor point back to the beginning
- Control-A moves the cursor to the beginning of the line
- Control-E moves the cursor to the end of the line
- Control-R allows you to search through the previous commands
- Control-L clears your screen and presents you with a fresh prompt

## Keep on learning

Here are some great resources to help you get more comfortable with the command line.

- [The Command Line Crash Course](http://cli.learncodethehardway.org/book/)
