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

Install
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

 =========end===========

GenesisH0
----------
now we are clone master litecoin <br>
clone GenesisH0 <br>
cd Desktop <br> 
git clone https://github.com/lhartikk/GenesisH0 <br>
openssl ecparam -genkey -name secp256k1 -out genesiscoinbase.pem <br>
openssl ec -in genesiscoinbase.pem -text > genesiscoinbase.hex <br>

now looking for GenesisH0 first <br>
Enter the GenesisH0 directory <br>
in terminal <br>
cd GenesisH0/ <br>

how to find time, on the open terminal or open a new terminal, type <br>

date +%s (COPY <font color="blue">TIMESTAMP RESULT </font>) <br>
-t <font color="blue"> 1317972665 </font> <br> 

(TODAY'S HEADLINE)  <br>
take from newspapers / magazines / web, about today's events <br>
(take the date / month / year, the event that happened) <br>

open the downloaded Genesiscoinbase, take the PUBKEY code and remove the mark (:, space) <br>
(PUBKEY FROM GENESISCOINBASE.HEX) <br>
0498afaa7c10b00d595b44cda02578b0e99b8ae9bb9e784b39dc16d05ae4e436167ee15d627cde8085b40042a226832f869b8d36547cadf3bdb62ab04d19bd6639<br>
nonce <br>
for nonce, while the value is free <br>
-n 1535594777 <br>

python genesis.py -a scrypt -z "<<TODAY'S HEADLINE>>" -p "<<PUBKEY FROM GENESISCOINBASE.HEX>>" -t <<PASTE TIMESTAMP RESULT>> -n <<WHATEVER INTEGERS>> <br>

example
---------- 
python genesis.py -a scrypt -z "Batampos, 30/Aug/2018, Menuju Parlemen" -p "0498afaa7c10b00d595b44cda02578b0e99b8ae9bb9e784b39dc16d05ae4e436167ee15d627cde8085b40042a226832f869b8d36547cadf3bdb62ab04d19bd6639" -t 1535594777 -n 2084524493 <br>

waiting until finish
---------- 
when it's finished <br>
04ffff001d010426426174616d706f732c2033302f4175672f323031382c204d656e756a75205061726c656d656e <br>
algorithm: scrypt <br>
merkle hash: 9e9533320d053ddbdb39cb59f1b1f9f5ddb1a13a42121bc974f3c5d7f417de72 <br>
pszTimestamp: Batampos, 30/Aug/2018, Menuju Parlemen <br>
pubkey: 0498afaa7c10b00d595b44cda02578b0e99b8ae9bb9e784b39dc16d05ae4e436167ee15d627cde8085b40042a226832f869b8d36547cadf3bdb62ab04d19bd6639 <br>
time: 1535594777 <br>
bits: 0x1e0ffff0 <br>
Searching for genesis hash.. <br>
genesis hash found! <br>
nonce: 2125880190 <br>
genesis hash: e0307acc3766d4bcd2c047da0dfb274d0352705e37b6a5613974c59423b89ece <br>

move folder
---------- 

enter the "Batamcoin" folder, change "Litecoin" to "Batamcoin" <br>

find ./ -type f -readable -writable -exec sed -i "s/Litecoin/Batamcoin/g" {} \; <br>
find ./ -type f -readable -writable -exec sed -i "s/LiteCoin/BatamCoin/g" {} \; <br>
find ./ -type f -readable -writable -exec sed -i "s/LTC/BAM/g" {} \; <br>
find ./ -type f -readable -writable -exec sed -i "s/litecoin/batamcoin/g" {} \; <br>
find ./ -type f -readable -writable -exec sed -i "s/litecoind/batamcoind/g" {} \; <br>
can be ignored <br>
find ./ -type f -readable -writable -exec sed -i "s/lites/batubesar/g" {} \; <br>
find ./ -type f -readable -writable -exec sed -i "s/photons/batukecil/g" {} \; <br>
find . -type f -print0 | xargs -0 sed -i 's/9333/2333/g'  <br>
find . -type f -print0 | xargs -0 sed -i 's/9332/2332/g' <br>
find . -type f -print0 | xargs -0 sed -i 's/19335/20331/g' <br>
find . -type f -print0 | xargs -0 sed -i 's/19444/20332/g' <br>

START MODIFY
---------- 

src/chainparams.cpp  <br>
src/chainparams.cpp Line 115, 214, 294 <br>
genesis = CreateGenesisBlock(1535610916, 2137156518, 0x1e0ffff0, 1, 50 * COIN); <br>

src/chainparams.cpp Line 117,216and Line 296  <br>
	assert(consensus.hashGenesisBlock == uint256S("genesis hash")); <br>

src/chainparams.cpp Line 118,217,297  <br>
assert(genesis.hashMerkleRoot == uint256S("merkle hash")); <br>

src/chainparams.cpp Line 53 <br>
const char* pszTimestamp = "pszTimestamp"; <br>

src/chainparams.cpp Line 54 <br>
const CScript genesisOutputScript = CScript() << ParseHex("pubkey”); <br>

src/chainparams.cpp  <br>
Line 80-81 , 184-185, 268-269 <br>
consensus.nPowTargetTimespan 0.5 * 24 * 60 * 60; // 3.5 days <br>
consensus.nPowTargetSpacing = 5 * 60; <br>

src/chainparams.cpp line 101,205 <br>
consensus.nMinimumChainWork = uint256S("0x0000000000000000000000000000000000000000000000000000000000000000"); <br>

change line 144,244,310 <br>
(  0, uint256("0xe0307acc3766d4bcd2c047da0dfb274d0352705e37b6a5613974c59423b89ece")) // Genesis <br>

src/chainparams.cpp  <br>
line 160-163 <br>
line 245-247 <br>
line 311 <br>
1535594777  // time <br>
0, <br>
0.0 <br>

//temporarily changed the last 1 digit only, 0-9, a-f <br>

src/chainparams.cpp Line 108-111   "Main" <br>
        pchMessageStart[0] = 0xfc; //whatever 2 digits hexadecimal <br>
        pchMessageStart[1] = 0xc1; //whatever 2 digits hexadecimal <br>
        pchMessageStart[2] = 0xb7; //whatever 2 digits hexadecimal <br>
        pchMessageStart[3] = 0xdc; //whatever 2 digits hexadecimal <br> 

src/chainparams.cpp Line 207-210 "Test" <br>
        pchMessageStart[0] = 0xfe; //whatever 2 digits hexadecimal <br>
        pchMessageStart[1] = 0xd3; //whatever 2 digits hexadecimal <br>
        pchMessageStart[2] = 0xc9; //whatever 2 digits hexadecimal <br>
        pchMessageStart[3] = 0xf2; //whatever 2 digits hexadecimal <br>

src/chainparams.cpp Line 287-290 "RegTest" <br>
        pchMessageStart[0] = 0xfb; //whatever 2 digits hexadecimal <br>
        pchMessageStart[1] = 0xc0; //whatever 2 digits hexadecimal <br>
        pchMessageStart[2] = 0xb6; //whatever 2 digits hexadecimal <br>
        pchMessageStart[3] = 0xdb; //whatever 2 digits hexadecimal <br>

src/chainparams.cpp Line 121-125 <br>
because it does not have a DSN, the one who works with BATAMCOIN is temporarily disabled <br>
	 vSeeds.emplace_back("dnsseed.batamco.in", true); <br>
//        vSeeds.emplace_back("seed-a.batamcoin.loshan.co.uk"); <br>
//        vSeeds.emplace_back("dnsseed.thrasher.io"); <br>
//        vSeeds.emplace_back("dnsseed.batamcointools.com"); <br>
//        vSeeds.emplace_back("dnsseed.batamcoinpool.org"); <br>
//        vSeeds.emplace_back("dnsseed.koin-project.com"); <br>

src/chainparams.cpp Line 223-225 <br>
//        vSeeds.emplace_back("testnet-seed.batamcointools.com"); <br>
//        vSeeds.emplace_back("seed-b.batamcoin.loshan.co.uk"); <br>
//        vSeeds.emplace_back("dnsseed-testnet.thrasher.io"); <br>

src/chainparams.cpp Line 128,130-133"Main" <br>
base58Prefixes[PUBKEY_ADDRESS] = std::vector<unsigned char>(1,25); //B <br>
base58Prefixes[SCRIPT_ADDRESS2] = std::vector<unsigned char>(1,25);  //B <br>
base58Prefixes[SECRET_KEY] =     std::vector<unsigned char>(1,25); // B <br>
base58Prefixes[EXT_PUBLIC_KEY] = boost::assign::list_of(0xbb)(0x88)(0xB2) (0x1E).convert_to_container<std::vector<unsigned char> >(); <br>
base58Prefixes[EXT_SECRET_KEY] = boost::assign::list_of(0xbb)(0x88)(0xAD)(0xE4).convert_to_container<std::vector<unsigned char> >(); <br>

src/chainparams.cpp Line 227,229-232  "Test" <br>
base58Prefixes[PUBKEY_ADDRESS] = std::vector<unsigned char>(1,85); //b <br>
base58Prefixes[SCRIPT_ADDRESS2] = std::vector<unsigned char>(1,85); //b <br>
base58Prefixes[SECRET_KEY]     = std::vector<unsigned char>(1,85);
base58Prefixes[EXT_PUBLIC_KEY] = boost::assign::list_of(0xbb)(0x35)(0x87) (0xCF).convert_to_container<std::vector<unsigned char> >(); <br>
base58Prefixes[EXT_SECRET_KEY] = boost::assign::list_of(0xbb)(0x35)(0x83)(0x94).convert_to_container<std::vector<unsigned char> >(); <br>

src/chainparams.cpp Line 317,319-322  "Regtest" <br>
base58Prefixes[PUBKEY_ADDRESS] = std::vector<unsigned char>(1,85); //b <br>
base58Prefixes[SCRIPT_ADDRESS2] = std::vector<unsigned char>(1,85); //b <br>
base58Prefixes[SECRET_KEY]     = std::vector<unsigned char>(1,85); <br>
base58Prefixes[EXT_PUBLIC_KEY] = boost::assign::list_of(0xbb)(0x35)(0x87)(0xCF).convert_to_container<std::vector<unsigned char> >(); <br>
base58Prefixes[EXT_SECRET_KEY] = boost::assign::list_of(0xbb)(0x35)(0x83)(0x94).convert_to_container<std::vector<unsigned char> >(); <br>

move to 
---------- 
delete all file/data in  MAIN dan TEST <br>
src/chainparamsseeds.h Line 11 <br>
	static SeedSpec6 pnSeed6_main[] = { <br>
	}; <br>
and line 15 <br>
	static SeedSpec6 pnSeed6_test[] = { <br>
	}; <br>
	#endif // BITCOIN_CHAINPARAMSSEEDS_H <br>

END MODIFY
---------- 
--move to -- <br>
Batamcoin>doc>man <br>
change litecoin to batamcoin <br>
Batamcoin>src>qt>res>icons <br>
change litecoin_splash.png to batamcoin_splash.png <br>

START RUN IN TERMINAL
---------- 
cd /Litecoin atau Batamcoin <br>
sudo chmod -c 777 autogen.sh <br>
sudo ./autogen.sh <br>
sudo ./configure <br>
sudo make <br>


Setup 2 virtual machine
---------------
Now we need to have at least one other connection to the network in order to mine. <br>
We can either set up another computer, or lease a VPS which allows us to set up a mining pool for others to mine batamcoin. <br>
 
But for just practice and demo purpose, we clone our previous VM. <br>
However, before we clone it, we need to make sure our network settings match the actual network adapter; <br>

VM 1 – Acting as Server <br>
A) Right-click on the VM =>Settings=>Network  <br>
Select Attached to: Bridged Adapter <br>
Name: [Drop down and select the correct adapter for your Host machine] <br>

B) Right-click on the VM =>Clone  <br>
Give a different name, eg Ubuntu-Server <br>
Check the “Reinitialize the MAC address of all network cards
Clone type ; “Linked clone” <br>

C) Start the Ubuntu-Server VM… and go to the hidden  <br>folder .batamcoin at the home folder <br>
(tip, use ctrl+h to show all hidden folders) and delete all  contents in it (to avoid having similar wallet as the Linked-VM). <br>
Create a new file name it batamcoin.conf  (the configuration file for a server); <br>
		
rpcuser=user <br>
rpcpassword=pass <br>
rpcbind=192.168.1.34:20332 <br>
rpcallowip=192.168.1.1/24 <br>
server=1 <br>
addnode=192.168.1.43 <br>

D) Go to network connection information to get the IP address; 192.168.xxx.xxx  <br>

VM 2 – Acting as Client (Miner) <br>

E) Now go back to the Linked-VM we used to clone (Linked Base for Ubuntu-Miner…..) <br>
Right-click on the VM =>Settings=>System=>Processor <br>
Increase the Processor(s) from 1 CPU to 4CPU (only if you have enough cores to spare, <br>
eg i7-8700 has 6Cores and 12 Threads… so you will see 12 CPUs, so you can spare 4 CPUs for mining) <br>
This will speed up the mining with higher Hash power. <br>

F) We shall use this as a client VM or miner node.  (It is not exactly necessary for a “client-server” configuration as peer-to-peer networks can toggle between modes, acting either as server or client via file sharing protocol, etc.)  <br>

Similarly, go to the hidden folder .batamcoin at the home folder and add a new file,  batamcoin.conf (unlike the server, do not delete the files under this directory!); <br>
	
rpcuser=user <br>
rpcpassword=pass <br>
rpcbind=192.168.1.43:20332 <br>
rpcallowip=192.168.1.1/24 <br>
server=1 <br>
addnode=192.168.1.34 <br>

now mining testing
----------
Batamcoin>src>qt> <br>
./batamcoin-qt <br>

in the application, click Help "Debug Windows" >> the Console tab type "generate nblocks" example "generate 5" <br>




