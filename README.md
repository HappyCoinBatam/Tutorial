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

sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 -y <br>
sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev -y <br>
sudo apt-get install libboost-all-dev -y <br>
sudo apt-get install software-properties-common <br>
sudo add-apt-repository ppa:bitcoin/bitcoin <br>
sudo apt-get update <br>
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y <br>
sudo apt-get install libminiupnpc-dev -y <br>
sudo apt-get install libzmq3-dev -y <br>
sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev  <br>qttools5-dev-tools libprotobuf-dev protobuf-compiler -y <br>
sudo apt-get install libqrencode-dev -y <br>

---install pip and scrypt <br>
sudo apt-get install python-setuptools python-dev build-essential -y <br>
sudo easy_install pip  <br>
sudo pip install --upgrade virtualenv  <br>
sudo pip install scrypt construct==2.5.2 <br>
