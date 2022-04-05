---
modified_date: 2020-12-31T10:47:56.000-08:00
tags:
- NAS
- synology
title: Synology Hyperbackup is disturbingly slow
description: 'Three Megabytes per second: the Hyperbackup software for Synology NAS
  is unbearably slow'
published: true

---
I recently upgraded my Synology DS115j to a [DS220J ](https://www.amazon.com/Synology-DiskStation-Business-Storage-Operating/dp/B097Z21C5W?crid=KK2TJOEA7Y4A&keywords=synology%2Bds220j&qid=1649178627&sprefix=synology%2Bds220j%2Caps%2C233&sr=8-3&th=1&linkCode=ll1&tag=thermal002-20&linkId=a63a5078ba7dbce41f59b5b6fd452880&language=en_US&ref_=as_li_ss_tl "DS220J")and a [10TB Western Digital Red Plus drive](https://www.amazon.com/s?k=WD+Red+plus+10+tb&crid=2TLKWOSWVI6Q1&sprefix=wd+red+plus+10+t%2Caps%2C150&linkCode=ll2&tag=thermal002-20&linkId=36b3135849d7ea2508d2dece9a1127bd&language=en_US&ref_=as_li_ss_tl). (I may earn a small commission from this link, thanks!)

The DS220J is much more responsive in the web-browser UI than the old clunker, and was relatively inexpensive. I am not transcoding video or anything, so the cheaper "J" model seemed like a good fit over the "plus/+" model. Generally, I am happy with it, but in retrospect, would have ponied up for the more expensive [DS220+](https://www.amazon.com/Synology-Bay-DiskStation-DS220-Diskless/dp/B087ZCBWFH?crid=3QCFGLHTFERV4&keywords=synology+ds222%2B&qid=1649179347&sprefix=synology+ds222%2B%2Caps%2C130&sr=8-3&linkCode=ll1&tag=thermal002-20&linkId=1cd1fc5ad53e7939832efef95e771c18&language=en_US&ref_=as_li_ss_tl)

A main reason for me to own a Synology is to use it as a versioned backup system (_a la_ Apple's MacOS _TimeMachine_) for the various shared folders on it (namely, Documents, Photos, Music). This functionality is achieved through the Synology Hyperbackup software for the DSM OS. I really like the general concept where the backup is stored to many types of targets: local disk (internal to DS220J), USB-attached hard drive, network server via Rsync, or even another Synology drive installed elsewhere.

Generally, Hyperbackup works fairly ok. I say "fairly ok", because I've experienced a few issues (such as a backup that became corrupted after transferring from the older DS115J, that luckily only allowed for read-only access. I was forced to re-create the backup).

I have used three different devices for the target backup device: old DS115j, external USB 3.0 HDD, and the internal Diskstation directory structure. In each case, the average speed is excruciating!

Luckily, I only have about 1 TB of data, but with the expectation of eventually backing up 10 TB, this is not good.. it would take on the order of a month to do a full backup or restore!

#### Calculate GB/day of backup

Throughput:  
3 MB/s * 60 s/min * 60 min/hr * 24 hr/day * 1/(1000 MB/GB) = **259.2 GB/day**

#### Days to fully backup 10 TB:

10 TB * 1000 GB/TB * 1/(259.2 GB/Day) = **38.58 Days**

### Root Cause

I'll update this post if I find one. I suspect it is due to an inefficient algorithm or method inherent to Hyperbackup rather than hardware-specific reasons. There are some posts on Reddit and Synology forums that voice similar concerns, although not to the extreme slowness of my example. Those other posts may have been for the "plus/+" models that have a much more powerful CPU, and despite that, they were still slow.

## Conclusion

I can only hope I don't need to rely on hyperbackup, and that as I add information to it, it can grow over years, rather than wait for 30 days to complete.

An alternative backup solution is to manually copy the files periodically in an ad-hoc fashion. Ughhh. Welcome to 1990.. To this method's benefit, my father has been doing this for decades and has access to all his data, from all time, in raw file format.