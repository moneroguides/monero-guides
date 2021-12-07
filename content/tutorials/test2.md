---
title: "Setting up P2Pool on Windows"
date: 2021-11-17T10:21:07Z
image: images/test_scrn2.png
description: "Learn how to set up p2pool on Windows"
type: "article"
layout: "article"
---

{{ youtube yfbvTksF9ic >}}


### Prerequisites:

- Kleopatra (GPG4Win) - https://www.gpg4win.org/download.html
- New Monero wallet address (primary)

.....................................................................

### INTRO

Hello and welcome to this tutorial on how to install P2Pool and start mining Monero.

P2Pool (https://p2pool.io/) is a decentralised pool which leverages a side chain to manage the active miners and their rewards.

In order to join the Monero P2Pool all you need to do is run the p2pool software as well as Xmrig.

Before getting started there are a couple of prerequisites: firstly you will need to have Kleopatra installed, we'll have a link for that down below in the description. You'll also need a Monero wallet address. This is so P2Pool has somewhere to send you precious Monero. Lastly you'll need to have at least 50GB of free disk space. 

This guide assumes no previous mining experience. If you already have xmrig and/or the latest version of the Monero daemon, you may wish to to look only at the P2Pool setup and skip the rest. 

.....................................................................

### CREATING THE WORKING FOLDER

Before doing anything, we're going to create a folder called 'monero-mining' in our root directory on the `C:` drive. We will be doing everything in this directory from this point on. Windows may flag Xmrig as a virus in the upcoming steps, so we'll need to create an exclusion rule for the folder.

To do this we'll need to go to the virus and threat protection settings. you can find this by typing it in the search bar or opening the start menu and typing in `virus`. Next, under **Virus and Threat Protection Settings**, click on **Manage Settings**. Scroll down until you see the **Exclusions** Section and choose **Add or remove exclusions**. Click **Add an exclusion**, choose **folder** and then navigate to the folder that you just created in the root directory.

......................................................................

### DOWNLOADING AND VERIFYING P2POOL

A link to the required installer for setting up your node and a connection to the P2Pool sidechain can be found in the description - https://github.com/WeebDataHoarder/p2pool-nsis/releases/
 
Once you locate the latest release, scroll down to the assets and download the installer, shasums and default config.

Datahoarder's public key can be found on each release page. Open up a text editor and copy the public key into the editor. We can save it as `key.txt`.  Then we'll need to open Kleopatra and import the key we just copied. Be sure to use this dropdown to select **any files** so that you can see the `key.txt` file. There is no need to counter sign it as trusted. The important thing is to see a certificate which matches datahoarder's key.

Next we want to verify the sums file. First click on **decrypt/verify** and navigate to the sha file you just downloaded.

We can see that the name on the certificate matches the key that we just imported.

Now to check that this is in fact the file we to be installing and not something sinister, let's go back to our `monero-mining` folder, `shift + right-click` and choose **open powershell here**. Type `Get-Filehash` and then the name of the file that you want to get the hash for, which is this case is the P2Pool installer. Fortunately we don't have to type in the whole thing. We can just start typing "P2" and then press `TAB` and it will completet the filename for us. Now we press `Enter` and it gives us the file hash. We can now open the shasum file and compare the hash within to the hash we just generated. Simply right click and open with your text editor of choice. We can see that this hash matches this line here. Which means that we have a match and that the file is safe to use.

............................................................................

INSTALLING P2POOL

Alright, now that we've done that it's time to install P2Pool. Right-click the install file and choose **Run as administrator**. Click **next** until you get to the part where you choose the install location. Install it to the same folder we have been working in. You'll now need a new Monero wallet address where you would like your mined Monero to go. After the setup as finished you'll see a new folder here in our `monero-mining` folder, you'll also see a shortcut has appeared on your desktop. This is how we will start the P2Pool software.

.....................................................................

SYNCHING THE BLOCKCHAIN (FROM SCRATCH)

If you've already downloaded Monero block-chain either because of a local node or wallet, go ahead and skip to the next section. For everyone else, follow this section carefully and skip over the next section. 

Before running P2Pool you will need to make sure you have enough space on your drive. 
During the initial setup we will be creating a very large file that can easily excede 40GB. 

If you're happy to procede then you should run P2Pool by double-clicking the icon that has just been created. We are now syncing a database file located in the p2pool folder with the Monero blockchain. This could take several hours so let's continue with the other parts of the setup in the meantime. If you have followed the steps in this section there is no need to view the next section entitled **IMPORTING A PREEXISTING BLOCKCHAIN**. So you can go ahead and skip over the next section and go straight through to setting up XMrig.

.....................................................................

IMPORTING A PREEXISTING BLOCKCHAIN

For those of you that already have the monero blockchain downloaded to you computer you will have two options. The first option would be to copy or move your files across to the p2pool/lmdb directory. You'll be able to find your preexisting lmdb folder in C:\ProgramData\bitmonero. Copy or move the lmdb folder to the root of our current p2pool folder.

If you'd prefer not to move or copy the existing blockchain file, you can simply tell p2pool where to look for it.

To do this right-click the start.ps1 file, choose edit, and go to line 60. Where it says data-dir we're going to change this from data-dir=. to `data-dir C:\ProgramData\bitmonero\` 

Now when we use the icon on the desktop to run p2pool, it will use the preexisting blockchain files. This means you'll only have to wait a short while while it synchs the most recent blocks.

.....................................................................

DOWNLOADING AND VERIFYING XMRIG

It's now time to install XMrig. If you already have this installed then feel free to skip this section.

Let's head over to the xmrig official github repository to get the latest release. The link to this page can be found down in the description. There are a lot of options here, for windows we're looking for the one that says gcc-win64 in the file name. don't forget to download both of the sums files as well. For convenience, we're going to download there files to the same folder we've been working in up until now.

https://github.com/xmrig/xmrig/releases

we're going to verify the download the same way as before so I'll move through this process a bit more quickly this time. The public key for xmrig can be found in a different location this time, check the video description for the link. 

- https://github.com/xmrig/xmrig/blob/master/doc/gpg_keys/xmrig.asc
- https://xmrig.com/docs/gpgpg-key 
(DON'T FORGET SUMS GET-FILEHASH)

Once again we're going to copy the key into a text file. We can use the same `key.txt` file from earlier. Now that we've got our files and the key we're going to open Kleopatra once again. First import the `key.txt` file. No need to countersign. Next choose **decrypt/verify** to verify the shasum files. Finally we need to go back into our `monero-mining` folder and get the file hash for the XMRig zip that we just downloaded. Open powershell and run `Get-Filehash` with the name of the zip file we just downloaded. Open the sums file and compare the two file hashes.

Great, we can see that there's a match so this means that the zip file is in fact the one we were supposed to download and it should therefore be safe to use. So let's go ahead and open it and extract the contents.

Before we go any further with our XMRig setup, Let's check on the P2Pool software. It's taken around 8 hours for it to sync on my machine and now that it has, it is very important to reboot.

You'll find a timestamp in the description so you can easily return to this point in the video after rebooting.

.....................................................................

XMRIG BENCHMARK AND CONFIGURATION

Welcome back. To continue getting XMRig set up, head into the extracted folder.

We're going to run `benchmark_1M.cmd`, let it run all the way through to make sure your system is stable. While this is running it's a good chance to chech that `HUGE PAGES` is enabled. This is quite important and will really improve your hash rate. If it doesn't say `permission granted` there'll be a link down in the description to help you solve this problem. Once that's complete your hashrate can be found here. Mine says 2157h/s. Take note of your hashrate as you'll need it in just a moment.

To make sure XMRig is using the correct configuration when it runs, datahoarder has kindly put one together for us. It's the config.json file we downloaded earlier. But we need to make one slight tweak before we continue.

In the user section we curently have "x+600000". We should replace that number with one equal to 30x your hash rate. For example my hashrate was 2157 so I would multiply that by 30 and I would put this number over here. We can now move this file into the xmrig folder. Replace the file in the destination.Let's also create a shortcut for xmrig and place it on the desktop.

.......................................................................

TIME TO MINE 

Alright, it's finally time to get our mining underway. So let's open p2pool by clicking on the desktop icon. We need to wait for it to finish synchronising before we open XMRig. You will know it's synched once you start receiving blocktemplates and see `depth = 0`. 

Finally we can run XMRig. Make sure you do this as an administrator otherwise you'll see this `FAILED TO APPLY MSR MOD` error. This will negatively impact your hashrate and quite significantly. Again, do make sure that `HUGE PAGES` says `permission granted`. If it doesn't, check the link in the description for help.

https://xmrig.com/docs/miner/hugepages

.....................................................................

P2P INTERFACE

To check that all you've done is actually paying off, there's a few things you can do. Firstly, xmrig should be recieving jobs from your local ip address. 

Secondly you can use console commands when in the p2pool terminal window. `status` will print the status of the side chain, your stratum server and the p2pserver. If everything went well you should see at least 1 connection under the stratumserver subheading. It should also report your estimated hash rate. 

As p2pool uses a pplns system you are only paid for your effort if you have a share in this window when a block is minted. For more information about PPLNS, please read the blog post by NiceHash linked below in the comments. 

https://www.nicehash.com/blog/post/how-mining-pools-distribute-rewards-pps-vs-fpps-vs-pplns#!

Under the sidechain heading you will see the number of shares you've submitted and an approximation of the reward you will recieve once a block has been minted. As we haven't submitted any shares this session there is no information available. 

Other commands can be found by typing `help`. For example you can set `loglevel` which will change how much is being logged out if you find the interface a bit too crowded. Log level 2 is a comfortable  setting for most people. To set it you can simply type `loglevel 2` and hit enter.

.....................................................................

PORT FORWRADING

There are two big incentives for miners to join p2pool. First is the low payout threshold and 0% fees. The other is the ability to sign up to the xmrvsbeast raffle. 

If it's your first time hearig about the xmrvsbeast raffle, here's what you need to know. 

The raffle exists to incentivise miners, especially those with low has rates. It currently does so by pointing large amounts of hashing power to your node for a given period of time.

It started quite recently at the beggining of 2021 and was set up by an anonymous group or individual. They started by setting up their own pool but with the advent of the P2Pool, the xmrvsbeast pool was closed and all the incentives moved to the P2Pool network.

If you would like to take part in the raffle, the next part of the video covers port forwarding for this purpose.

In order for the hashing power of xmrvsbeast to reach your node you will need to open up your stratum server to the world.
Port forwarding can be a tricky business, but in general both your router and your computer need to have this port forwarded. Since every router is different, we wont' be covering port forwarding on routers in this video. But for Windows, here's what we need to do:

Open the Windows start menu and begin typing the word "Firewall". It should be the first result. Once here, click on **Advanced Settings** then choose **Inbound Rules**. Create a new rule. This rule is for a port. Click Next. We want TCP and then the port number which is 3333. Allow the connection. Give it a name, and that's it. We've opened port 3333 which is your default Stratum server. 

It is also reccomended to open ports 18080 (Monero daemon) and 37889 (P2Pool Peer Network) for better connectivity with the rest of the network. Although this is not mandatory.

.....................................................................

SIGNING UP TO THE RAFFLE

Once you have the correct port forwarded you'll need to head on over to the xmrvsbeast website linked in the description.

https://xmrvsbeast.com/p2pool/ 

At the bottom of the landing page you'll find some useful links. The first is the boost dashboard. As well as a raffle, there is also a boost system which provides bonus hashrate to miners sequentially. So regardless of your luck you can always expect a little boost from time to time.
The second link explains in more detail the rules of the raffle and provides a page to register which we will be heading to in a moment. As well as a page for viewing your history as a raffle participant.

Select register/update. This is where you enter the infomation required to find your node. This includes your monero address which is used to manage the raffle, your public ip address and the port you have forwarded. The token field should be left blank for new registrations.

If you don't know your public ip address you can find it using the powershell and the command `ipconfig` or you can more simply check on a 3rd party site. I like to choose the websites of vpn providers such as mullvad https://mullvad.net/en/ or https://nordvpn.com/

A successful registration should look something like this. Write down your token, this is very important.

We can check double check our registration has been successful by heading over to the history page and entering our XMR address and the token we were issued with.

If you have any troubles with this step please head over to the xmrvsbeast subreddit and search for similar issues before posting. A link to this can be found in the description.

https://www.reddit.com/r/xmrvsbeast

.....................................................................

MONERO.OBSERVER

You can easily check your progess remotely by visiting https://p2pool.observer/

Here you can use your monero address to search and find your individual progress. As we're new to mining we'll get an error. Only once you have begun finding shares will you see infomation about your miner and its progress. 

To find out how often you may produce shares, head back to the main page and select the average share time calculator, punch in your hashrate and you'll receive an estimate.

Let's take a look at another miners progress to see an example. Here you can see statistics from the miner including average effort, blocks found and share positions. Here the shares move from right to left with time unlike the p2pool program.

Below this you will see infomation about each payout and the shares which enabled those payouts at the bottom. 

.....................................................................

This pool is only possible because of the hard work of contributers. the main repository for p2pool can be found in the description below.
https://github.com/SChernykh/p2pool

If you're interested to know more about it's featuresa nd how it works, including how to set things up on a different OS, this is the place to come. And at the bottom of this page you will find a donation address. The people who work on these things do it mostly for love rather than money, so every donation goes to keeping them motivated.

Well, that's all for this video. Thanks so much for watching and happy mining.

