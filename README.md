Tutorial Batamcoin 0.15
=====================================

[![Build Status](https://travis-ci.org/batamcoin-project/batamcoin.svg?branch=master)](https://travis-ci.org/batamcoin-project/batamcoin)

https://batamcoin.org

First install virtualbox
----------------

install & create Virtual Machine
	Go New=>Name and operating system =>
	Name: Ubuntu16A
	Type: Linux
	Version: Ubuntu (64-bit)
=>Next => Memory size (4096MB if possible as C++ is memory hungry) =>Next 
=> Hard disk (Create a virtual hard disk now) => Create
=> Hard disk file type => VDI (default)
=> Storage on physical hard disk (Dynamically allocated) => Next
=> File location and size (25GB)  => Create
=> Start => Click folder to select virtual optical drive (iso file)
=> ubuntu-16.04.3-desktop-amd64 =>open => Start

Installation steps
-------

=> Install Ubuntu 
=> Check “Download updates while installing Ubuntu”
=> Optional “Install third-party software ….. “
=> Continue
=> Accept “Erase disk and install ubuntu” => Install Now
=> Write the changes to disk ? => Continue
=> Where are you? Select or type your location => Continue
=> Choose your keyboard layout “English (US)”  => Continue
	Your name			: Ubuntu
	Your computer’s name	: Ubuntu-VirtualBox
	Pick a username		: ubuntu
	Choose a password		: password
	Log in automatically
=>Continue  (about 3-5 mins….)  => restart

Share Folder
-------------------

Because we use virtualbox, then we install an application to share folders
=>Devices => Insert Guest Additions CD image… => Run  => insert your password

-----------RUN IN TERMINAL---------
sudo apt-get install module-assistant
sudo m-a prepare
cd /media {Username}  
ls
cd {Username}
cd VBox_GAs_5.2.16/
sudo sh VBoxLinuxAdditions.run
sudo adduser {username} vboxsf
sudo reboot

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

Translations
------------

We only accept translation fixes that are submitted through [Bitcoin Core's Transifex page](https://www.transifex.com/projects/p/bitcoin/).
Translations are converted to Batamcoin periodically.

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.
