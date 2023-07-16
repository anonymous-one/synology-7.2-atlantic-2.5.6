This is the most recent (as of this writing) kernel driver for the aquantia / marvell 2.5 / 5.0 / 10.0 gbe adapters.

This is essentially:

**atlantic.ko
Version 2.5.6
Compiled for DSM 7.2 64570**

The standard kernel module that comes with DSM 7.2 64570 is 2.4.3.

I have not had a chance to test this yet, but ideally... Connect via one of the onboard non-AQC ports... rmmod, insmod, test... If all works, you should be able to backup /lib/modules/atlatic.ko, and replace /lib/modules/atlantic.ko.

Modinfo from the stock version:

```description:    Marvell (Aquantia) Corporation(R) Network Driver
author:         Marvell
version:        2.4.3.0
license:        GPL v2
firmware:       aquantia/91B1.fw
firmware:       aquantia/87B1.fw
firmware:       aquantia/80B1.fw
srcversion:     CEDB2A10892173CAD860859
alias:          pci:v00001D6Ad000007B1sv00007053sd00001009bc*sc*i*
alias:          pci:v00001D6Ad000007B1sv00007053sd00001001bc*sc*i*
alias:          pci:v00001D6Ad0000D107sv00007053sd00001001bc*sc*i*
depends:        crc-itu-t
retpoline:      Y
vermagic:       4.4.302+ SMP mod_unload
sig_id:         PKCS#7
signer:         Synology Kernel Module Signing Certification Authority
sig_key:        02
sig_hashalgo:   sha384
signature:      AA:01:80:8A:18:0D:B4:F1:A6:7A:93:5A:1D:B1:74:5E:96:E9:11:25:
                46:5B:FD:42:23:5C:34:BA:E7:58:7A:95:CE:80:3E:17:76:C3:04:23:
                5A:01:9A:74:F0:71:29:BF:21:82:4D:ED:24:7E:C6:D0:A2:9E:D8:1B:
                4D:5C:97:B6:88:54:45:46:A8:D4:8C:42:00:CD:9C:3F:C7:73:7C:D4:
                F6:E1:AB:0C:E8:88:75:FB:FA:7A:8C:A7:BE:45:BA:41:C6:E2:5B:D2:
                2E:33:B3:93:75:C9:B1:74:06:4A:4A:C7:C6:E2:E8:4C:EC:C5:7C:F3:
                52:70:D9:1F:26:B9:9C:B5:0D:32:3F:67:14:C9:29:AC:8C:CC:8F:DB:
                79:12:CC:EA:BD:67:0D:B5:C9:F7:8E:72:E1:26:8A:C5:FA:03:F9:D6:
                05:BB:53:9D:D0:E8:5A:A9:1A:50:4D:46:68:1D:A1:13:82:65:6A:C8:
                B9:5B:CA:B0:71:26:CD:37:67:A5:16:12:87:2B:79:05:39:CA:C1:0B:
                F4:6A:E7:C8:87:09:9D:38:8D:CB:21:5B:D2:03:05:51:37:7B:C9:FB:
                19:3C:6D:46:99:D7:68:68:E5:FE:C8:D9:C8:84:4F:DA:86:C8:AC:9C:
                8F:A6:00:A0:43:77:57:E1:9C:C4:C9:97:24:12:0B:BC
parm:           aq_ptp_offset_forced:Force to use the driver parameters (uint)
parm:           aq_ptp_offset_100:PTP offset for 100M (uint)
parm:           aq_ptp_offset_1000:PTP offset for 1G (uint)
parm:           aq_ptp_offset_2500:PTP offset for 2,5G (uint)
parm:           aq_ptp_offset_5000:PTP offset for 5G (uint)
parm:           aq_ptp_offset_10000:PTP offset for 10G (uint)
parm:           aq_itr:Interrupt throttling mode (uint)
parm:           aq_itr_tx:TX interrupt throttle rate (uint)
parm:           aq_itr_rx:RX interrupt throttle rate (uint)
parm:           aq_rxpageorder:RX page order override (uint)
parm:           aq_rx_refill_thres:RX refill threshold (uint)
parm:           aq_fw_did:Use FW image for this DID (array of uint)
parm:           aq_fw_sid:Use provisioning data for this SID (array of uint)
parm:           aq_force_host_boot:Force host boot (array of uint)
parm:           aq_new_filters_enabled:New RX filters enable (uint)
parm:           aq_enable_wa:Quirk bits to enable HW workarounds (int)
parm:           aq_enable_ptp:Enable PTP (bool)```

Modinfo from this updated version:

```description:    Marvell (Aquantia) Corporation(R) Network Driver
author:         Marvell
version:        2.5.6.0
license:        GPL v2
firmware:       mrvl/91B1.fw
firmware:       mrvl/87B1.fw
firmware:       mrvl/80B1.fw
srcversion:     02D8BF365F1799D03CA1642
alias:          pci:v00001D6Ad000093C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000094C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000011C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000012C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000034C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000014C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000000C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000004C0sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000092B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000091B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000089B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000088B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000087B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000080B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000012B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000011B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000009B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000008B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000007B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad000000B1sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D109sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D108sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D107sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad0000D100sv*sd*bc*sc*i*
alias:          pci:v00001D6Ad00000001sv*sd*bc*sc*i*
depends:        crc-itu-t
vermagic:       4.4.302+ SMP mod_unload
parm:           aq_ptp_offset_forced:Force to use the driver parameters (uint)
parm:           aq_ptp_offset_100:PTP offset for 100M (uint)
parm:           aq_ptp_offset_1000:PTP offset for 1G (uint)
parm:           aq_ptp_offset_2500:PTP offset for 2,5G (uint)
parm:           aq_ptp_offset_5000:PTP offset for 5G (uint)
parm:           aq_ptp_offset_10000:PTP offset for 10G (uint)
parm:           aq_ptp_gpio_hightime:PTP GPIO high time (uint)
parm:           sleep_delay:uint
parm:           aq_itr:Interrupt throttling mode (uint)
parm:           aq_itr_tx:TX interrupt throttle rate (uint)
parm:           aq_itr_rx:RX interrupt throttle rate (uint)
parm:           aq_rxpageorder:RX page order override (uint)
parm:           aq_rx_refill_thres:RX refill threshold (uint)
parm:           debug:Default debug msglevel (uint)
parm:           aq_fw_did:Use FW image for this DID (array of uint)
parm:           aq_fw_sid:Use provisioning data for this SID (array of uint)
parm:           aq_force_host_boot:Force host boot (array of uint)
parm:           aq_enable_wa:Quirk bits to enable HW workarounds (int)
parm:           aq_enable_ptp:Enable PTP (bool)```
