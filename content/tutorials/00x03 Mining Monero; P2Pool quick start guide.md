---
title: "00x03 Mining Monero; P2Pool quick start guide"
date: 2022-07-15T10:00:00Z
image: images/00x03.png
description: "Instructions for mining Monero with the official GUI"
type: "article"
layout: "article"
---
{{< rawhtml >}}<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
<iframe src="https://invidio.xamh.de/embed/IQCXfbUXo90" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" allowfullscreen title="01x04 Using Monero With Enhanced Privacy"></iframe></div>{{< /rawhtml >}}
<br/>

# Mining Monero; P2Pool quick start quide

## Prerequisites:

* gpg (Linux)
* Kleopatra (Windows) - [GPG4WIN](https://www.gpg4win.org)
* +50GB of free disk space

<hr/>

### INTRO

Hello and welcome. In this tutorial we'll be showing you how to quickly and easily start mining Monero.

To do this we'll be downloading and installing the official Monero wallet GUI. This software is built by the community and distributed by the Monero core team.

It has a convenient interface which will allow you to start mining via [P2Pool](https://github.com/SChernykh/p2pool/), the most effective and simple way to start earning Monero with your home PC!

Before getting started there are a couple of prerequisites:  Firstly, as a Windows user you will need to have Kleopatra installed while Linux and Mac users should have gpg installed. This software is used to verify the contents of the files and folders we'll be downloading.

**Mac users beware, this tutorial doesn't contain specific advice for you. However, you should be able to follow the linux instructions without too much trouble.**

In addition to this software you'll need 50GB or more disk space free. This is necessary for downloading either a full of pruned copy of the blockchain.

This guide assumes no previous mining experience. If you already have xmrig and/or the latest version of the Monero daemon, you may wish to to look at the official [P2Pool repo](https://github.com/SChernykh/p2pool/) for more specific instructions. 


### DOWNLOADING AND VERIFYING THE MONERO GUI WALLET

We're going to start by visiting [getmonero.org](https://www.getmonero.org/), the official website of the Monero Core Team. 

Feel free to browse the site and learn more about Monero before continuing. 

When you're ready, go ahead and click on the Downloads tab.

The software we're interested in is the "Monero GUI Wallet". To download it, scroll down until you reach the "Downloads" subheading. 

Next, click and download the software which matches both your hardware and operating system.

As I'm using Ubuntu, I'll be choosing the 64bit Linux version.

To check that these are the files intended for use by the creators we’ll need two important pieces of information:

- Either a signed copy of the file hashes; or a signature file ending with '.asc'
- The public key of the person who signed them

We can find these files using the "Show hashes to verify your download" drop-down menu.

The first link gives us a copy of the signed hashes. Simply right click and *save link as* to download this text file.

To locate binaryfate's public key, we should head back to the getmonero site and click on the link entitled *in the source code*. 

This link has taken us directly to binaryfate's public key. To download a copy, simply right click on the *Raw* button and click *save link as*.

For the rest of the process please take a look at our guide entitled [01x01 - Importing Public Keys & Verifying Hashes](https://moneroguides.org/tutorials/01x01-importing-public-keys-and-verifying-hashes/). Feel free to stop after watching the section entitled **VERIFYING SIGNATURES & HASHES**, as you can then return to this guide.

Make sure to use the files you have downloaded now rather than the ones from the other video. The process is exactly the same otherwise. 

The following two sections cover installation for Linux and windows separately. Feel free to use the time stamps to get to the section that suits you best.


### INSTALLING THE MONERO GUI WALLET - LINUX

By now you should have downloaded and verified the contents of your download.

Now that's done, we're going to start by extracting the contents of this zipped folder. To do this, we need to simply right click and select *Extract Here*. 

Feel free to place this folder somewhere memorable, or alongside your other program files.

Let's take a look through the folders. We're looking for the file labelled *monero-wallet-gui.AppImage*. Once found, we can start the program by double clicking.

We'll first be asked if we want to create a desktop entry, I'm going to select yes. This will provide me with a handy icon to select each time I want to start mining.

After that, we are ready to go.

To continue, please skip over the next section which is meant for Windows users only.


### INSTALLING THE MONERO GUI WALLET - WINDOWS

By now you should have downloaded and verified the contents of your download.

To install the software, simply extract the contents of the zip file and then double click on the installer.

We'll be prompted to navigate through a welcome screen and then a  licence agreement. The Monero Wallet GUI is free and open source software, so this agreement is shorter than you may think.

After clicking accept and next we will now need to choose where to install the software. I'm going to choose the default location.

Next, we need to choose the location for our blockchain data. Don't worry about this 90GB requirement, this has changed and will be covered again in the next section.

Once again we'll select next. I want the Monero software to appear in my start menu, so I'll be leaving this section as it is and moving on.

I don't want a desktop icon... I just want to install the software :) 

And there we have it.

Just a couple of things to do before we continue. Let's start by opening the software from the start menu.

We are now prompted to set some firewall rules. I am going to deselect public networking and allow private networking. In the future, this will allow other computers in my network to use the blockchain data hosted on this computer.

With that done, it's time to add a rule to Windows defender.

Windows may flag the Monero software as a virus in the upcoming steps, so we'll need to create an exclusion rule for the install folder.

To do this we'll need to go to the virus and threat protection settings. You can find this by typing it in the search bar or opening the start menu and typing in **virus**.

Next, under Virus and Threat Protection Settings, click on Manage Settings. Scroll down until you see the *Exclusions* section and select *Add or remove exclusions*. Click *Add an exclusion*, choose folder and then navigate to the folder that the Monero Wallet GUI was installed to.

Finally, we're ready to continue.

### SETTING UP YOUR WALLET AND NODE

Welcome to the Monero wallet GUI.

Feel free to set the language of the interface before continuing. 

Next we're going to select *Advanced mode*.

We're going to want to create a brand new wallet. This is because the primary address of your miner will be visible to the P2Pool network. It is good to think of this as a wallet dedicated to mining only. 

We're then prompted to choose a name for a wallet, and a save location. I'm going to be saving my wallet to an encrypted drive, which I set up earlier.

We're also given an opportunity to record our new seed phrase and the restore height. These are important pieces of information and act as the keys to the wallet.

After making a copy of this information, select next and then enter a new, strong password to encrypt the wallet file. We recommend using password generators usually bundled with managers such as Bitwarden and KeePassXC.

When you're ready to continue, hit next.

Mining using this GUI is only possible with the availability of a local node. Hosting a local node is both great for the security of others and your own personal privacy.

To run your own local node you need to download a copy of the blockchain. The entire Monero blockchain is currently around 130GB in size. It's constantly increasing in size and is something you should keep in mind.

For those who don't have this amount of memory to spare, you can alternatively download a pruned copy of the blockchain, this currently takes around 50GB of space.

Depending on your own circumstances you will want to select different options. We're going to download a full copy of the blockchain to the default location, so all that's left to do is click next once again.

To finish up, all we need to do is review our settings and select *Create wallet* and then enter the password we chose in the previous step.

In the bottom left-hand corner of the landing page you'll notice that the current network status is labelled *Synchronising*. Be prepared to wait a significant amount of time for this process to complete. It can take anywhere from 12 hours to a week. The time it takes to complete will depend on your blockchain choices, your hardware and your internet speed.

Writing the blockchain to an SSD will guarantee the best performance.

Currently we’re only leeching the blockchain from the P2P network and sharing is caring after all, so we’ll want to enable seeding as well. To do this, we’re going to have to set special rules in the firewall to allow incoming connections for the Monero Peer Network (18080) and the P2Pool Peer Network (37889) on both our computers and routers.

For information on how to do this, you can check out our [node setup guide](https://moneroguides.org/tutorials/01x02-setting-up-your-own-node/)

Once your node is synchronised (as you can see mine is now) it will be time for you to move on to the next section.


### TIME TO MINE 

Alright, it's nearly time to get our mining underway. The software is now synchronised with the rest of the network and we've now only got a few more settings to change. 

We're now to going to select the *settings* tab from the menu and then *node*. 

For now we're going to stop the daemon with the button provided.

Next we're going to add the following flags to the box provided. You can find a copy of them in the video description.

`--disable-dns-checkpoints --enable-dns-blocklist`

These options help to ensure reliability and security. Once you've entered those settings, you can restart the daemon.

To access the mining menu, click on the advanced tab.

Here we want to change mode to P2Pool and confirm we're using the *mini* side chain, which is recomended for all new users. We're going to leave everything else as default for now. 

Let's click *Start mining*.

To continue, the Monero software will need to install the additional P2Pool software. It will automatically install it to the same location and all we have to do is select *yes*.

It will take a short while to download and when it's done, you'll receive a prompt.

It's finally time to start mining! So let's go ahead and select *Start mining* once more.

At first you will see your status change to *Connected + Mining* and once everything is up and running, the Monero software will then display your hashrate. Your hashrate, is the speed at which your computer is securing the network, the greater your hashrate, the greater your rewards!


### SIGNING UP TO THE XMRVSBEAST RAFFLE

There are two big incentives for miners to use the P2Pool. First is the low payout threshold and 0% fees and the other is the ability to sign up to the xmrvsbeast raffle. 

If it's your first time hearing about the xmrvsbeast raffle, here's what you need to know. The raffle exists to incentivise miners, especially those with low powered machines to contribute the security of the network.

You can sign up to the raffle via the [xmrvsbeast website](https://xmrvsbeast.com/p2pool/). Before heading over there, let's first copy our new address to the clipboard.

Registration gives you access to two different reward streams. The first is a sequential boost. You can take a look at the boost dashboard via the link. For more details about how it works, just click on *rules*.

Let's head back to the main raffle basboard. Once again, for more details, click on *rules*. Now that we've seen how this all works, let's register.

To register, you'll need to enter the primary address of the new wallet you created. The token field should be left blank for new registrations. 

As we're new to mining, we'll initially receive an error message. This is because we're yet to prove that we're actively mining. Only once we've started making contributions to the network will we be able to register successfully. 

Once you've registered successfully, make a note of the token you are issued with, as this will be required in the future!
With your address and token, you can then check the history of your wins, using the link on the main page.

If you have any troubles with these steps please head over to the [xmrvsbeast subreddit](https://www.reddit.com/r/xmrvsbeast) and search for similar issues before posting.


### MONERO.OBSERVER

You may be wondering how to know when you can successfully sign up to the raffle.

You can easily check the progress of your miner remotely by visiting [mini.p2pool.observer](https://mini.p2pool.observer/).

Here you can use your Monero address to search and find your individual progress. Once again, as we're new to mining we'll get an error. Only once we've begun finding shares will we see information about the miner and its progress. Once we see a valid share, we can then sign up for the raffle.

To find out how often you may produce shares, head back to the main page and select the average share time calculator, punch in your hashrate and you'll receive an estimate.

Let's take a look at another miners progress to see an example. Here you can see statistics from the miner including average effort, blocks found and share positions. Here the shares move from right to left with time .

Below this you'll see information about each payout and the shares which enabled those payouts at the bottom. 


### OUTRO
Well, there you have it! Hopefully you're now up and running and earning those sweet rewards. As a parting note, please remember this pool is only possible because of the hard work of contributors. The main [repository for p2pool](https://github.com/SChernykh/p2pool) can be found in the description below.

If you're interested to know more about it's features and how it works, including how to set things up on different OSs, this is the place to come. And at the bottom of this page you will find a donation address. The people who work on these things do it mostly for love rather than money, so every donation goes to keeping them motivated.

We sincerely hope this guide has helped you on your way to participating in Monero ecosystem. If you're interested in more in depth guides, please check out the other videos in our channel. And if you found this useful and want to send us a tip, our address can be found on screen now.

Anyway, that's all from us this time around. So goodbye for now!

~moneroguides
