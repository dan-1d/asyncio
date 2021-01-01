---
modified_date: 2021-01-01 10:47:56 -0800
published: false
tags:
- NAS
- synology
title: Synology Hyperbackup is disturbingly slow
description: The Hyperbackup software for Synology NAS is unbearably slow at 3 MB/s
  average

---
I recently upgraded my Synology DS115j to a DS220J and a 10TB Western Digital Red Plus drive. The DS220J is much more responsive in the web-browser UI than the old clunker, and was relatively inexpensive. I am not transcoding video or anything, so the cheaper "J" model seemed like a good fit over the "plus/+" model. Generally, I am happy with it.

A main reason for me to own a Synology is to use it as a versioned backup system (_a la Apple TimeMachine_) for the various shared folders on it (namely, Documents, Photos, Music). This functionality is achieved through the Synology Hyperbackup software for the DSM OS. I really like the general concept where the backup is stored to many types of targets: local disk (internal to DS220J), USB-attached hard drive, network server via Rsync, or even another Synology drive installed elsewhere.

Generally, Hyperbackup works fairly ok. I say that, because I've experienced a few issues (such as a backup that became corrupted after transferring from the older DS115J, that luckily only allowed for read-only access. I was forced to re-create the backup.

The backup 