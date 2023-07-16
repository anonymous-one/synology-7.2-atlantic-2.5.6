This is the most recent (as of this writing) kernel driver for the aquantia / marvell 2.5/5.0/10.0gbe cards.

This is essentially:

atlantic.ko
Version 2.5.3
Compiled for DSM 7.2 64570

The stock driver that comes with DSM 7.2 64570 is 2.4.3.

I have not had a chance to test this yet, but ideally... Connect via one of the onboard non-AQC ports... rmmod, insmod, test... If all works, you should be able to backup /lib/modules/atlatic.ko, and replace /lib/modules/atlantic.ko.
