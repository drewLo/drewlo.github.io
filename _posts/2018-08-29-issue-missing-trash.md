---
layout: post
title:  "[Open] Unable to move files/dir to Trash bin"
date: 2018-08-29 14:10:00 -0700
published: true
comments: true
tags: GNU+Linux issue open
---

# Problem:

- File browser (nautilus) can't find Trash directory when deleting files on other partitions aside from system partition.
- Files that live in the system partition get moved to trash folder with no issues.
- Since nautilus cannot find the files, it offers to delete the files permanently. This allows the system to still be usable, but only having the option to permanently delete files is obviously suboptimal.

### Error msg: 
- `$FILE can't be put into trash, do you want to delete it immediately?`
- `Unable to find or create trash directory for /path/to/pending/delete/file.foo`

### Information: 
- OS: Fedora
- Non-system Partitons Format: NTFS (listed as `fuse`)
- System Partition Format: EXT4
- Both `.Trash` and `.Trash-$UID` directories are in the partition mount points. ie. `/home/dlo/soma/.`
- At some point, during attempts at fixing the problem, the option in the right-click context menu stopped listing `Move to Trash`, and instead now displays `Delete Permanently` (see below).

![Trash Not Found][example]

## Attempts:
- `sudo` `chown` | `chmod` seem to have no effect. The folder(top directory, ie. partition mount point) remains owned by root:root.
- Set the sticky bit for the directories as well. using `sudo chmod +t .Trash` and `.Trash-$UID`. No observable effect.
- Drive was remounted with alternative options: `mount -o remount,default_permissions,allow_other /media/dlo/soma`. No observable effect.

### Considerations:
- Nautilus may not have the correct permissions.
  + `sudo nautilus` throws several errors related to g_dbus and dfails to launch.
  + `gksu` doesn't exist on my system, it might be able to be installed but I want to explore other options first.

## Results:
- TBA

[example]: ../images/gnome-no-trash.jpg "Trash not found"
