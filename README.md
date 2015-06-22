# samba-dfree-script

Samba often reports the the remaining space of the root drive, which may be undesirable if you have a pool mounted in a single location.  This script reports the remaining space of the drive with the least available space in /mnt.  This can be convenient if you have several drives mounted in the same place as because it highlights the lack of space which would otherwise be hidden.

![samba_wrong] ![samba_right]

Installation Procedure:

1. Place this file in /usr/local/bin (anywhere will do, but this is the recommended location)
2. Make sure it is owned by root:root and has the permissions 755 (-rwxr-xr-x) applied to it
3. Edit /etc/samba/smb.conf and add the line below  [global]

```
dfree command = /usr/local/bin/dfree_pool_min
```

Notes

- This script will function even if the drives are not of the same capacity.
- All of the online scripts I saw had some form of `df $1` which caused an error for me.

Refer to the [Samba documentation][1] for more information on the dfree command.

[samba_right]: https://raw.githubusercontent.com/rfordyce/samba-dfree-script/master/images/samba_right.png "right"
[samba_wrong]: https://raw.githubusercontent.com/rfordyce/samba-dfree-script/master/images/samba_wrong.png "wrong"
[1]: https://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#idp59614672
