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
+ At the command prompt (in the black window), you type:

```
mkdir vagrant-ubuntu
cd vagrant-ubuntu
vagrant init ubuntu/trusty32
```


