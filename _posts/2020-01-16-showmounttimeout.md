---
layout: post
title: NFS: clnt_create: RPC: Port mapper failure - Timed out
---

After setup NFS server, you try to use `showmount` command to list out shared entries in server, but you get below error:

```
[root@client ~]# showmount -e server
clnt_create: RPC: Port mapper failure - Timed out
```

Then you checked firewall setting, port 111(rpcbind) and 2049(nfs) TCP are open. What you don't know is showmount use UDP by default. So, if you want to use `showmount`, please open 111/udp also.

Or you can just use 

```
# mount -t nfs4 / /mnt
```

That's because NFS4 doesn't use rpcbind, so 111/udp isn't used in that case.
