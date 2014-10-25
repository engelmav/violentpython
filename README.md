# WTF?

We want to be able to share screens so we can see what we're doing, and we want to be able to code and mess around using Linux. We also want to be able to do that without messing up our computers. So below are instructions on how to set this all up.

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

Start up the virtual machine and login to it.

```
vagrant up
vagrant ssh
```

Now you will be able to share files between Windows and the virtualized Linux operating system. We can test it out.

+ Open up SublimeText and type one line:

```python
print "I'm a python script."
```
+ Go to `File -> Save`
+ Navigate to C:\<username>\vagrant_ubuntu\violentpython
+ In the `Name:` field, type the name of the file as `test.py`.
+ Hit the `Save` button.

Just notice one thing - that the text in SublimeText is now colored. This is because SublimeText now recognizes that this is a Python file, because of the `.py` at the end of the filename.

Anyway, since we saved this `test.py` to the `violentpython` folder, we should now be able to see it in our virtualized Linux environment. Let's check.

+ At the Linux command prompt, type `ls -l /violentpython`.

You should see something like this:

```bash
vagrant@vagrant-ubuntu-trusty-32:~$ ls -l /violentpython
total 4
-rw-rw-r-- 1 vagrant vagrant 27 Oct 25 18:07 test.py
```

There's your `test.py` file. `ls` is a Linux command that means "list files". Google it for more information, if you want.

Now we can **run** the script. from within the same Linux environment, by typing the following:

```bash
vagrant@vagrant-ubuntu-trusty-32:~$ python /violentpython/test.py 
I'm a python script
```

And you'll see the output `I'm a python script`. That is, of course, the script you wrote.
