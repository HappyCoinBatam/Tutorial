Tutorial Batamcoin 0.15
=====================================

[![Build Status](https://travis-ci.org/batamcoin-project/batamcoin.svg?branch=master)](https://travis-ci.org/batamcoin-project/batamcoin)

https://batamcoin.org

First install virtualbox
----------------

install & create Virtual Machine <br>
	Go New=>Name and operating system => <br>
	Name: Ubuntu16A <br>
	Type: Linux <br>
	Version: Ubuntu (64-bit) <br>
=>Next => Memory size (4096MB if possible as C++ is memory hungry) =>Next  <br>
=> Hard disk (Create a virtual hard disk now) => Create <br>
=> Hard disk file type => VDI (default) <br>
=> Storage on physical hard disk (Dynamically allocated) => Next <br>
=> File location and size (25GB)  => Create <br>
=> Start => Click folder to select virtual optical drive (iso file) <br>
=> ubuntu-16.04.3-desktop-amd64 =>open => Start <br>

Installation steps
-------

=> Install Ubuntu  <br>
=> Check “Download updates while installing Ubuntu” <br>
=> Optional “Install third-party software ….. “ <br>
=> Continue <br>
=> Accept “Erase disk and install ubuntu” => Install Now <br>
=> Write the changes to disk ? => Continue <br>
=> Where are you? Select or type your location => Continue <br>
=> Choose your keyboard layout “English (US)”  => Continue <br>
	Your name			: Ubuntu  <br>
	Your computer’s name	: Ubuntu-VirtualBox <br>
	Pick a username		: ubuntu <br>
	Choose a password		: password <br>
	Log in automatically <br>
=>Continue  (about 3-5 mins….)  => restart <br>

Share Folder
-------------------

Because we use virtualbox, then we install an application to share folders <br>
=>Devices => Insert Guest Additions CD image… => Run  => insert your password <br>

-----------RUN IN TERMINAL--------- <br>
sudo apt-get install module-assistant <br>
sudo m-a prepare <br>
cd /media {Username}  <br>
ls <br>
cd {Username} <br>
cd VBox_GAs_5.2.16/ <br>
sudo sh VBoxLinuxAdditions.run <br>
sudo adduser {username} vboxsf <br>
sudo reboot <br>

Intall
-------

first if you haven't installed GIT, install it first <br>
enter the terminal is at home <br>
clone litecoin //back to home <br>
sudo apt-get install git  <br>
git clone https://github.com/litecoin-project/litecoin <br>
on home change the name of the "litecoin" folder to "Batamcoin"  <br>
cd Batamcoin <br>
Check the location of the branch first, so that when you edit the  code, no version error occurs <br>
git branch -a <br>
git checkout remotes/origin/0.15 <br>

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
