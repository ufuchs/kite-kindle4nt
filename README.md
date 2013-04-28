kite-kindle4nt
==============

### Research

There are reports of different kinds of runlevels/init scripts at 

```
[02-18-2012, 06:14 AM]
http://www.mobileread.com/forums/showpost.php?p=1970489&postcount=15

[09-01-2012, 07:02 AM]
http://www.mobileread.com/forums/showpost.php?p=2205271&postcount=62
```

Both posts were published at a time when runlevel 3 and 5 were missing:

```
ln: /etc/rc5.d/S62kite: No such file or directory
ln: /etc/rc3.d/K07kite: No such file or directory
```

Thus the original kite script could fail only.

On the other hand, my Kindle from October 2012

```
Original System Software Version: 025-H3_yoshi-181303 Sat Jan 12 20:40:53 PST 2013
```

(after an update!) includes all run levels 0-6.

The version on the 'Settings' page shows 'Version: Kindle 4.1.1(181303 0025)'

### But what does not?

1. /etc/rc3.d is not longer the default shutdown run level. 
   It's /etc/rc6.d.

2. The invocation of 'kite' at '/etc/rc5.d/S62' is too early.
   Kite depends on the DBus subsystem.
   But the DBus subsystem has been invoked only just a moment ago.
   (Maybe a concurrencies problem?)

### Interim Solution

The invocation was shifted from 'S62kite' to 'S81kite'.

On the other side, when the call comes too late, you are expecting some artifacts on the boot screen.

_Note:_ 

If a text file contains binary data like 'kite.sh', some text editors won't be  working correctly.

'Sublime Text', Vim e.g. works fine, while the GEdit  fails completely.

### Summary

Look at the version number and then decide which option appears true for you.

If your version number is less than 4.1.1, then followed the advice from the second website.

If the version number is equal to 4.1.1, then tried my 'kite.sh'.

To instantly install the script, use the usbNetwork.