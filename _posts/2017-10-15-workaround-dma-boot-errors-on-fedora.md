---
layout: post
title: Workaround DMA boot errors on Fedora
tags: linux, fedora, grub2
---

I had to fix a laptop with Fedora with boot errors like:

```
[   11.631123] ata5.00: failed command: READ FPDMA QUEUED
[   11.631147] ata5.00: cmd 60/f0:68:18:09:80/00:00:04:00:00/40 tag 13 ncq 122880 in
[   11.631207] ata5.00: status: { DRDY }
```

I found out, that you can workaround the errors by disabling "Native Command Queuing" or short "NCQ".

You do that by open `/etc/default/grub`, edit the line `GRUB_CMDLINE_LINUX_DEFAULT` and add `libata.force=noncq`.

Finally update the boot manager by:

```bash
mkconfig-grub -o /boot/grub2/grub.cfg
```
