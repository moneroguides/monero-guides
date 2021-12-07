---
title: "P2Pool-Mini Side Chain"
date: 2021-11-17T10:21:07Z
description: "New P2Pool side chain for low hash rate miners"
image: /images/startps1.png
type: "article"
layout: "article"
---

# P2Pool-Mini Side Chain
## UPDATE
\
\
If your hash rate is bellow 50Kh/s please consider the following link; https://xmrvsbeast.com/p2pool/sidechains.html

Follow the instructions on this this page for the mini pool. 

Make sure, the replace the existing peers file. Then edit your start.ps1 file. Edit line 90  so that it now reads 'Start-Process .\p2pool.exe -ArgumentList "--wallet $Wallet","--config mini_config.json","--p2p 0.0.0.0:3788" -Wait -NoNewWindow'
\
\
![startps1](/images/startps1.png)
