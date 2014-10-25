# Download skype

Windows

[Debian](https://wiki.debian.org/skype)

etc...

# Acquire Violent Python

There is a PDF out there that I cannot put here. Otherwise, [purchase at Amazon](http://amzn.com/1597499579 ).

# Get Vagrant

Vagrant is a virtual machine manager. It will help provide us with entire environments to build up and destroy as we need throughout our experimentation.

+ Download it from [here](https://www.vagrantup.com/downloads.html).
+ Install it.

# Get Virtualbox

Virtualbox actually runs our virtual environment. 

+ Download it from [here](https://www.virtualbox.org/wiki/Downloads). For Windows, it will be the "Windows hosts" link on that page.
+ Install it.

# Create a virtualbox and manage it with Vagrant

We choose a popular Linux distribution to start with. Here are the steps.

## For Windows

+ Open a command prompt by clicking Start and typing `cmd`, and pressing `Enter`. A black window with white text will pop up.
+ At the command prompt (in the black window), type the following, hitting enter after each line:

```
mkdir vagrant-ubuntu
cd vagrant-ubuntu
vagrant init ubuntu/trusty32
vagrant up
```

What you did here was create a virtual Linux environment that you will be able to work in. Now let's start it up and login to it. Type the following:

```
vagrant up
vagrant ssh
```

Your command prompt will now be something like:

```
vagrant@vagrant-ubuntu-trusty-32:~$ 
```

You are in a different operating system now. We will work from here.

# Get a text editor

This is for writing longer chunks of Python code. Download SublimeText [here](http://www.sublimetext.com/3).
Install it.

# Saving and running Python scripts

Let's back up a bit. On your command line where you have `vagrant@vagrant-ubuntu-trusty-32:~$`, type the following:

```
exit
vagrant halt
mkdir violentpython
```

We have exited our virtualized Ubuntu Linux environment, killed it, and created another folder called `violentpython`.

Now we're going to configure our vagrant virtual machine manager a bit by hand, so that we can share files easily between your Windows machine, and your virtualized Ubuntu Linux machine.

+ Open up `SublimeText`.
+ Go to `File -> Open File`
+ Navigate to c:\<username>\vagrant-ubuntu
+ Double click the file titled `Vagrantfile`
+ When that opens, just do `Cntrl-F` and type `config.vm.synced_folder`.
+ On that line, remove the pound sign frmo the beginning, and change the line to read exactly as so:

```
config.vm.synced_folder "violentpython", "/violentpython"
```  


