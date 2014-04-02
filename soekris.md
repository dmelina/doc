Soekris 6501-70
===============

Unboxing
--------

![Soekris unboxing](https://raw.githubusercontent.com/dmelina/doc/master/img/unboxing.jpg)

Premier boot
------------

Utiliser un cable série/USB et configurer minicom de la manière suivante.

    # Machine-generated file - use "minicom -s" to change parameters.
    pu port             /dev/ttyUSB0
    pu baudrate         19200
    pu bits             8
    pu parity           N
    pu stopbits         1


Premier boot.

    comBIOS ver. 1.41c  20121115  Copyright (C) 2000-2011 Soekris Engineering.
    
    net6501
    
    2048 Mbyte Memory                        CPU Atom E6xx 1600 Mhz 
    
    
    SATA AHCI BIOS ver. 0.61 20121115  Copyright (C) 2003-2011 Intel Corporation
    
    Controller Bus#02, Device#06, Function#00: 02 Ports, 01 Devices
      Port-00: Hard Disk, INTEL SSDSC2BW120A4            
        Port-01: No device detected
    
        Soekris USB Expansion ROM ver. 1.01  20111203
    
    
        Initializing Intel(R) Boot Agent GE v1.3.72
        PXE 2.1 Build 089 (WfM 2.0)
    
         Slot   Vend Dev  ClassRev Cmd  Stat CL LT HT  Base1    Base2   Int 
         --------------------------------------------------------------------
         00:00:0 8086 4114 06000005 0007 0000 00 00 00 00000000 00000000 
         00:23:0 8086 8184 06040000 0107 0010 08 00 01 1FFF1000 A0FFA000 10
         00:24:0 8086 8185 06040000 0107 0010 08 00 01 3FFF2000 A2FFA100 11
         00:25:0 8086 8180 06040000 0107 0010 08 00 01 5FFF4000 A4FFA300 05
         00:26:0 8086 8181 06040000 0107 0010 08 00 01 0FFF1000 00FFA000 09
         00:31:0 8086 8186 06010000 0003 0000 00 00 80 00000000 00000000 
         02:02:0 8086 8804 0C031002 0106 0010 00 00 80 A0000B00 00000000 09
         02:02:1 8086 8805 0C031002 0106 0010 00 00 80 A0000C00 00000000 09
         02:02:2 8086 8806 0C031002 0106 0010 00 00 80 A0000D00 00000000 09
         02:02:3 8086 8807 0C032002 0106 0010 00 00 80 A0000E00 00000000 09
         02:06:0 8086 880B 01060102 0107 0010 00 00 00 00000000 00000000 11
         02:08:0 8086 880C 0C031002 0106 0010 00 00 80 A0004800 00000000 10
         02:08:1 8086 880D 0C031002 0106 0010 00 00 80 A0004900 00000000 10
         02:08:2 8086 880E 0C031002 0106 0010 00 00 80 A0004A00 00000000 10
         02:08:3 8086 880F 0C032002 0106 0010 00 00 80 A0004B00 00000000 10
         02:10:1 8086 8811 07000201 0107 0010 00 00 80 00001041 A0004D00 09
         02:10:2 8086 8812 07000200 0107 0010 00 00 80 00001049 A0004D10 09
         02:12:2 8086 8817 0C800000 0106 0010 00 00 80 00000000 A0005000 05
         02:12:3 8086 8818 0C090000 0106 0010 00 00 80 00000000 A0005200 05
         03:00:0 111D 803A 0604000E 0107 0010 08 00 01 3FFF2000 A2FFA100 
         05:00:0 8086 10D3 02000000 0107 0010 08 00 00 A1000000 00000000 09
         06:00:0 8086 10D3 02000000 0107 0010 08 00 00 A2000000 00000000 10
         08:00:0 111D 803A 0604000E 0107 0010 08 00 01 5FFF4000 A4FFA300 
         10:00:0 8086 10D3 02000000 0107 0010 08 00 00 A3000000 00000000 10
         11:00:0 8086 10D3 02000000 0107 0010 08 00 00 A4000000 00000000 11
    
          1 Seconds to automatic boot.   Press Ctrl-P for entering Monitor.
    
          Intel(R) Boot Agent GE v1.3.72
          Copyright (C) 1997-2010, Intel Corporation
    
          PXE-E61: Media test failure, check cable                                       
          PXE-M0F: Exiting Intel Boot Agent.
    
          No Boot device available, enter monitor.
    
    
          comBIOS Monitor.   Press ? for help.
    
          > ?
          comBIOS Monitor Commands
    
          boot [drive][:partition] INT19 Boot
          reboot                   cold boot
          download                 download a file using XMODEM/CRC
          flashupdate              update flash BIOS with downloaded file
          time [HH:MM:SS]          show or set time
          date [YYYY/MM/DD]        show or set date
          d[b|w|d] [adr]           dump memory bytes/words/dwords
          e[b|w|d] adr value [...] enter bytes/words/dwords
          i[b|w|d] port            input from 8/16/32-bit port
          o[b|w|d] port value      output to 8/16/32-bit port
          run adr                  execute code at adr
          cmosread [adr]           read CMOS RAM data
          cmoswrite adr byte [...] write CMOS RAM data
          cmoschecksum             update CMOS RAM Checksum
          set parameter=value      set system parameter to value
          show [parameter]         show one or all system parameters
          ?/help                   show this help

Install
-------

Download du ramdisk et du booloader i386 depuis un ftp OpenBSD et rendre disponibles ces fichiers par TFTP.

    pxeboot
    bsd.rd

Configurer le DHCP.

    host gw {
          hardware ethernet XX:XX:XX:XX:XX:XX;
          fixed-address YY.YY.YY.YY;
          next-server ZZ.ZZ.ZZ.ZZ;  
          filename "pxeboot";             
    }

On tape reboot.

    CLIENT MAC ADDR: 00 00 24 D0 99 48                                             
    CLIENT IP: X.X.X.X  MASK: X.X.X.X  DHCP IP: X.X.X.X         
    GATEWAY IP: Y.Y.Y.Y 
    probing: pc0 com0 pci pxe![2.1] mem[620K 2046M a20=on]                         
    disk: hd0+*                                            
    net: mac 00:00:24:d0:99:48, ip X.X.X.X, server Z.Z.Z.Z
    >> OpenBSD/i386 PXEBOOT 3.19                                       
    boot> stty com0 19200       
    boot> set tty com0   
    switching console to com0
                             >> OpenBSD/i386 PXEBOOT 3.19
    boot> bsd.rd                                         


Quand on vous pose la question de vouloir setter sur com0 le boot et la console, vous dite mais bien sûr :)

    CONGRATULATIONS! Your OpenBSD install has been successfully completed!
    To boot the new system, enter 'reboot' at the command prompt.
    When you login to your new system the first time, please read your mail
    using the 'mail' command.

