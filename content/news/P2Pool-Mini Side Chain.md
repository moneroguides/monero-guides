---
title: "P2Pool-Mini Side Chain"
date: 2021-11-17T10:21:07Z
description: "New P2Pool side chain for low hash rate miners"
image: /images/startps1.png
type: "article"
layout: "article"
---

# P2Pool-Mini Side Chain
#### UPDATE for windows users
\
\
If your hash rate is below 50Kh/s please consider switching to P2Pool-mini

Since P2Pool version 1.7, you can do this by editing line 90 so that it now reads ```Start-Process .\p2pool.exe -ArgumentList "--wallet $Wallet","--mini","--p2p 0.0.0.0:37888" -Wait -NoNewWindow```
\
\
![startps1](/images/startps1.png)
