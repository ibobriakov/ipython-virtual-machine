Quick Start Instructions
=================================


In order to start the Vagrant-based virtual machine for Python environment, there are just a few easy steps to follow:

1) Download and install the latest copy of VirtualBox (https://www.virtualbox.org/) for your operating system
Although additional working knowledge of VirtualBox could be helpful, just accomplishing an installation is sufficient. However, see an important note below for Windows and Linux users that may require you to adjust your computer's BIOS settings for virtualization
The version of VirtualBox used as of this writing is 4.2.x. Type "VirtualBox --help" in a terminal to get version information if you already have it installed.

2) Download and install Vagrant (http://www.vagrantup.com/) for your operating system
It is highly recommended that you take a moment to read Vagrant's excellent "Getting Started" guide as a matter of initial familiarization
If you already have Vagrant installed, be sure that it's running version 1.2 or higher by typing "vagrant -v" in a terminal
The creator of Vagrant has written a book about it entitled Vagrant: Up and Running (http://oreil.ly/160VQcv)

3) Checkout source code of the virtual machine from this GitHub repository to your machine using Git or with the download links at the top of the main GitHub page.
Windows users should install Git for Windows (http://msysgit.github.io/) as it comes bundled with an SSH client that might come in handy later if you'd like to easily login to your virtual machine guest with Vagrant. (See screenshots and notes below. It is critical that you choose the option that includes an SSH client.)
Although you could opt to download the latest version of the source code from GitHub as a zip file (link to archive), basic familiarization with Git is likely to serve you well in your programming endeavors and is encouraged
In a terminal, navigate to the top level directory of the source code checkout that contains Vagrantfile.
On a Windows system, look for a Command Prompt program that's likely somewhere under your "Accessories" menu.

4) Run the following command from within the top level directory that contains your Vagrantfile: vagrant up
The first time you run this command, Vagrant will prompt you to download a base image for your virtual machine called precise64, which is an Ubuntu 12 Linux image. It may take anywhere between 10 and 30 minutes to download the base image and install the necessary updates and 3rd party packages depending on your connection speed.
In the event that you are running a 32-bit system, you'll need to change "precise64" to "precise32" in your Vagrantfile.
You should disable any settings which may allow your system to go into a sleep or hybernation mode while your virtual machine initially bootstraps.

What Happens Next

What should happen at this point is that Vagrant will use the Vagrantfile and Chef-based configuration management directives to download a Virtualbox base image and configure it. The first time you vagrant up, it takes ~15-45 minutes on average to download the ~323MB base image and then download/install critical updates and 3rd party packages. This time is largely dependent upon your Internet connection speed and hardware.
When all of the dependencies are installed, Vagrant will start the IPython Notebook server automatically on the virtual machine, map a shared directory onto your host machine, and configure the necessary ports for you to use your web browser to experience IPython Notebook.
When Vagrant finishes configuring your virtual machine, your terminal will return you back to a prompt. The final lines of its output should read something like the following:

[2013-07-27T01:45:27+00:00] INFO: runit_service[ipython] enabled [2013-07-27T01:45:27+00:00] INFO: Chef Run complete in 1553.918395 seconds [2013-07-27T01:45:27+00:00] DEBUG: Cleaning the checksum cache [2013-07-27T01:45:27+00:00] INFO: Running report handlers [2013-07-27T01:45:27+00:00] INFO: Report handlers complete [2013-07-27T01:45:27+00:00] DEBUG: Exiting

    At this point, an IPython Notebook server is running on your virtual machine, and you can access it from the web browser that you normally use on your host machine. Navigate to http://localhost:8888 and read the instructions in the "Chapter 0 - Preface" notebook to get started!
        There is nothing else to do with the virtual machine aside from a shutting it down when you'd like to stop working and recover the memory on your guest machine. (See the "Vagrant Cheat Sheet" below.)
        The virtual machine does not provide you with a desktop or graphical user interface. It runs an IPython Notebook server that you can connect to with your guest machine. The fundamental value proposition is that the virtual machine makes it possible to isolate and automate all of the configuration management for all example code in Mining the Social Web so that you don't have to do any of it yourself.
        Although not absolutely necessary, it still would be a worthwhile endeavor to learn how to vagrant ssh into the virtual machine and get more comfortable working with developer tools in a terminal environment. Take it one step at a time.

Vagrant Cheat Sheet

You are strongly encouraged to peruse Vagrant's documentation online to get a basic understanding of how it works. Once you have a general working knowledge, the following commands are likely to be the primary ones that you'll want to know how to use. Anytime you run these commands, it needs to be in the top level source code directory in which your Vagrantfile is located. Your Vagrantfile provides the basis for which the commands operate.
Essential Commands

    vagrant up - Starts your virtual machine.
    vagrant status - Tells you if your virtual machine is running.
    vagrant suspend - Saves the state of your virtual machine. (Similar to putting it to sleep.)
    vagrant resume - Restores a suspended virtual machine. (Similar to waking it up from sleep.)
        After your first vagrant up, a suspend/resume operation only takes a few seconds.
        Destroying your virtual machine means that you'll need to wait through the ~20 minute boostrap process the next time that you vagrant up.

Commands for Advanced Users

    vagrant halt - Shuts down your virtual machine.
        After your first bootstrap, a vagrant up only takes about one minute to complete.
    vagrant destroy - Destroys your virtual machine to the state of its base image.
        After you destroy a virtual machine, a vagrant up takes the full ~20 minutes to complete.
    vagrant ssh - Logs you into your virtual machine over SSH and provides a terminal.

Troubleshooting

    Linux/Windows users running on non-Apple hardware may experience problems running Vagrant that are related to BIOS settings
        If you are running on non-Apple hardware such as a Dell laptop or any other system running Windows or Linux, you may very well need to review and adjust your machine's BIOS settings in order to enable virtualization, which is likely disabled by default. If you're not familiar with "BIOS settings", think of it as a special control panel that allows you to adjust some very specialized hardware specific settings. When you reboot your system, you will usually see a message that explains how to enter into your system's BIOS settings and it usually involves pressing a particular key within a few seconds from the time it displays.
        In the BIOS settings for a Dell system, look for "Virtualization" options that may be embedded into options or menus related to "POST Behavior." The settings should provide binary options for "Off" and "Enabled" with a description to the effect of "This field specifies whether a Virtual Machine Manager (VMM) can utilize the additional hardware capabilities provided by Intel(R) Virtualization Technology. It is likely the case that the VMM technology is disabled by default, so you would want to adjust this setting to enable the VMM technology.
        If in the course of trying to use Vagrant to startup your Virtualbox you encounter an error to the effect of "No VT-x or AMD-V CPU extension found. Reason VERR_VMX_MSR_LOCKED_OR_DISABLED", it is almost definitely the case that your BIOS settings will need to be adjusted.
    Windows users should check to see that Git, Vagrant, SSH and other software packages are properly installed by typing "git", "vagrant", and "ssh" in a command prompt. If it is not installed, you'll get back a error message indicating that no such command could be found. If it is installed, you'll get back a message from the program indicating how to use it.
    If you experience troubles of any kind that you can't handle yourself, reach out on Twitter, Facebook, or better yet, file an issue at GitHub to request help
    Advanced users (who despite all attempts at convincing to use the virtual machine still prefer to run with their own installation) may benefit from reviewing the Chef-based configuration management in the deploy folder that encapsulates the steps required to get a good environment working with a minimal Linux base image. It's the exact set of steps that are used by Vagrant during configuration to bootstrap the virtual machine.

Consult (or contribute to) the Virtual Machine Installation Page on the wiki or open a ticket if you experience any problems.
Git and GitHub

In the event that you've never used a version control system such as Git to obtain or manage source code, be assured that it's well worth the investment to learn Git fundamentals. The first two chapters of http://gitscm.com/ are particularly worth the 15 or so minutes that it takes to complete, and you'll also find that Stack Overflow also contains a plethora of answers to common Git questions and best practice guidelines.

The absolute minimum Git skills that you'll want to know for consuming the source code of this book include:

    git clone - With git, you clone a repository to get its source code, and you'll need to git clone git@github.com:ptwobrussell/Mining-the-Social-Web-2nd-Edition.git to get source code for this repository. (The repository URL is provided in the right margin of https://github.com/ptwobrussell/Mining-the-Social-Web-2nd-Edition if you missed it.)
    git status - You can check the status of your repository by typing git status in the source code directory that you cloned. A common reason that you'll use git status is to determine if there are updates in the remote repository that you can pull down.
    git pull - Whenever the maintainer of a repository makes an update, you can pull the update by simply typing git pull in the source code directory that you cloned.
    git checkout - You can use git checkout to checkout a file you may have modified to restore it to its previous state.

As you become more comfortable with Git, you may want to fork a Git repository, commit changes to it, and push your changes to the master branch on GitHub. Consult http://gitscm.com/ for more information on how to do these things when you are ready to make that additional leap.

You are certainly able to download a zip archive of a GitHub repository's source code (look for the "Download ZIP" button in the right margin), but doing so would be a bit ironic. This book is all about the social web, and you'd be avoiding the premier social coding platform that hosts its project code. GitHub is inherently social, and there are benefits to participating that you can't gain any other way besides plugging in, being part of the community, and applying some Git fundamentals to contribute from time to time. Forking code, opening pull requests, and otherwise contributing within the boundaries of the GitHub platform tooling is much easier than you might initially think because GitHub delivers such a tremendous user experience. Take a few extra minutes to checkout the source code from GitHub instead of downloading a zip archive. You'll be glad that you took those steps.
"Git for Windows" Installation Screenshots

The following screenshots may be helpful as references for Windows users who are installing Git for Windows.


Windows users should opt to install the developer tools while installing Git for Windows in order to get SSH, which allows Vagrant's "vagrant ssh" command to seamlessly work.


Logging into your virtual machine (should you need or desire to do so for advanced troubleshooting) is as easy as "vagrant ssh" so long as you have an SSH client in your path


Once you have run "vagrant up" and your virtual machine is up and running, you essentially operate as though the virtual machine is just a piece of software running like any other. For example, you'll operate in your web browser just like normal to access IPython Notebook, which is where you'll spend all of your time. The nice thing about the virtual machine experience is that it allows you to use your host operating system as usual, although it encapsulates all of the messy configuration management details to a well-known and highly controlled environment.
Thank You!

Please file tickets here on GitHub if you experience any troubles whatsoever, and thanks again for your interest in this class. The goal in providing you with a completely turn-key machine experience is so that you can get the most out of the book and its source code -- not to divert your attention into unnecessary system configuration issues. Feedback on ways to improve this experience is always welcome, and pull requests are especially appreciated.
