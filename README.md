#### Before you start:
##### How to open a terminal on Mac and Windows

###### Mac

1. Using Spotlight search:
at the top right corner of your screen you can see a "magnifier" icon. By clicking on that a window will show up. Type the application you want - "terminal" and the Spotlight will give you some suggestions from where you can select terminal
2. Using Launchpad:
in the left side of the application Dock you can see a "rocket" icon in a silver circle.
When you click on that you will see the list of your applications, and in the top-middle, you can see a search box, type "terminal" and you will see the terminal icon, click on it and you should have terminal launched.

###### Windows
1. Standard Windows terminal:

    Go to Start panel
    Write "cmd" in search input field
    After "cmd" program is found you can execute it
    After succesful execution you will see black screen with command promp, where you can run commands

2. Enchanced Windows terminal (console)
Alternatively, you can install Console2 application (http://www.softpedia.com/get/System/OS-Enhancements/Marko-Bozikovic-Console.shtml), where you can have multiple tabs, change fonts and few other enchancements

##### How to change and create directories
When you succesfully opened terminal, you can perform simple operations with directories.
###### ls - shows all folders in current location:
    ls

###### cd - change location:
    cd test1 - will move you into "test1" folder
    cd .. - will move you one level up 

###### mkdir - make folder:
    mkdir test2 - will make folder "test2" inside current location

###### rmdir - remove folder:
    rmdir test2 - will remove folder "test2"

Quick Start Instructions
=================================
In order to start the Vagrant-based virtual machine for Python environment, there are just a few easy steps to follow:

#### 1) Download and install VirtualBox (https://www.virtualbox.org/)

#### 2) Download and install Vagrant (http://www.vagrantup.com/)

#### 4) Open a terminal window

#### 5) Go to the folder where you want to store the Vagrant virtual machine for the class (e.g., /Users/Panos/) :
    cd /Users/Panos

#### 6) Create a directory to store the Vagrant virtual machine for the class:
    mkdir DealingWithData
    cd /Users/Panos/DealingWithData

#### 7) Download this zip file: "I MAY NEED YOU TO PUT IT IN DROPBOX OR SOMEWHERE" and store in the folder that you created

#### 8) Go to the folder that you created and start Vagrant:

    cd /Users/Panos/DealingWithData
    vagrant up
[Note: this may take 15-30 minutes]
The first time you run this command, Vagrant will prompt you to download a base image for your virtual machine called precise64, which is an Ubuntu 12 Linux image. It may take anywhere between 10 and 30 minutes to download the base image and install the necessary updates and 3rd party packages depending on your connection speed.
In the event that you are running a 32-bit system, you'll need to change "precise64" to "precise32" in your Vagrantfile.
You can edit Vagrantfile in a simple text editor of your choice (such as Notepad/++, textit, Sublime etc.)
You should disable any settings which may allow your system to go into a sleep or hybernation mode while your virtual machine initially bootstraps.

Right now, your virtual machine is running

You can connect to machine in a command line:

    vagrant ssh

After that you will be connected to this machine and can implement different Unix commands

You can access the iPython server at http://localhost:8888/ where you
can see the iPython notebooks that we will be using for the class