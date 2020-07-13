
<a name="contents"/>

# Table of Contents

1. [ Table of Contents](#tableofcontents)
1. [ Installation](#installation)
   1. [ Unpacking Platina Cluster Head](#unpackingplatinaedgedevice)
   1. [ Rack-mounting Platina Cluster Head](#rackmountingplatinaedgedevice)
1. [ Administration](#administration)
   1. [ Quick Start Guide](#quickstartguide)
   1. [ General Architecture](#generalarchitecture)
      1. [ BMC Processor](#bmcprocessor)
      1. [ Intel Processor](#intelprocessor)
      1. [ Linux](#linux)
      1. [ Platina GOES Service](#platinagoesservice)
   1. [ Admin Privilege](#adminprivilege)
   1. [ Redis Database/Interface](#redisdatabaseinterface)
   1. [ QSFP28 Ports](#qsfp28ports)
   1. [ Set Media Type and Speed](#setmediatypeandspeed)
   1. [ Persistent Configuration](#persistentconfiguration)
   1. [ BGP](#bgp)
   1. [ Appendix 1: Redis Fields Guide](#appendix1redisfieldsguide)
      1. [ Fields that can be set in Platina’s Redis:](#fieldsthatcanbesetinplatinasredis)
      1. [ Stats Counter Update Interval](#statscounterupdateinterval)
      1. [ Read-only Redis Fields](#readonlyredisfields)
      1. [ Packages](#packages)
      1. [ Physical link state (as reported by switch ASIC)](#physicallinkstateasreportedbyswitchasic)
      1. [ Linux Packet/Byte counters](#linuxpacketbytecounters)
      1. [ Port Counters](#portcounters)
      1. [ Interface MMU Counters](#interfacemmucounters)
      1. [ Interface Pipe Counters](#interfacepipecounters)
      1. [ fe1 counters](#fe1counters)
      1. [ Eth0 stats](#eth0stats)
      1. [ EEPROM contents](#eepromcontents)
   1. [ Appendix 2: BMC Redis](#appendix2bmcredis)
      1. [ Connecting via IPv4](#connectingviaipv4)
      1. [ Connecting via IPv6 Link Local](#connectingviaipv6linklocal)
      1. [ Notable BMC Redis Fields](#notablebmcredisfields)
      1. [ PSU Information](#psuinformation)
      1. [ Power Monitor Information](#powermonitorinformation)
1. [ Software and Firmware Updates](#softwareandfirmwareupdates)
      1. [ Upgrading Coreboot](#upgradingcoreboot)
      1. [ Upgrading Linux Kernel](#upgradinglinuxkernel)
      1. [ Upgrading GOES](#upgradinggoes)
      1. [ Upgrading Coreboot, Linux Kernel, and GOES in one command](#upgradingcorebootlinuxkernelandgoesinonecommand)
      1. [ Updating the BMC Firmware](#updatingthebmcfirmware)
      1. [ Additional Information](#additionalinformation)
         1. [ Download the flash ROM and Coreboot images](#downloadtheflashromandcorebootimages)
         1. [ Getting to the BMC Console](#gettingtothebmcconsole)
1. [ Support](#support)


<a name="installation"/>

# Installation

## Unpacking Platina Cluster Head

The shipped package includes the following items:
 * 1 Platina Cluster Head with model number matching the packing slip
 * 2 AC power cords
 * 1 console cable with RJ45 to DB9 adapter for use when connecting the console direct to a laptop or other host.
 * 1 rack mount ear kit
 * 1 footpad kit

![](images/01-ll-optics.png)

## Rack-mounting Platina Cluster Head

This procedure is used to rack mount the Platina Cluster Head to a rack. It requires two people. Refer to the pictures below for the procedure. If Platina Cluster Head will be free-standing on a bench, then this procedure can be skipped and the footpad kit can be installed for bench use.

![](images/02-box.png)

1. Install the front rack mount ear kit, as shown in the first picture above.
2. Install the rear mount kit, as shown in second picture above if the rack is a 4-post rack. These brackets are not required if the rack is a 2-post rack.
3. Install the device in the rack. One person should lift the device into the rack to align the front rack brackets with the marked holes. A second person should secure the device in the rack using four rack-mounting screws (not provided).
4. If using the rear brackets, slide in the second portion and adjust until holes are align. Secure in place using rack-mounting screws (not provided).
5. Connect AC power to Platina Cluster Head.
6. Verify basic switch operation by checking the status of the switch status LEDs. When operating normally the LEDs should be green.

![](images/03-box.png)

<a name="administration"/>

# Administration

<a name="quickstartguide"/>

## Quick Start Guide

Please refer to the quick start guide included with the unit for
hardware package/unpackage instructions, MAC addresses, port labeling,
field replaceable unit labeling, and other general instructions.

<a name="generalarchitecture"/>

## General Architecture

The PSW-3001-32C contains a 32x100GE switch with hardware forwarding up to
3.2Tbps via the Broadcom Tomahawk ASIC. Built into the device is a
4-core Intel Broadwell DE CPU with 16GB RAM and 128GB SSD. There is also
a separate BMC ARM processor with 2GB of DRAM and 2GB of uSD. The high
level block diagram is as follows:

![](images/ConfigGuide_image1.png)

<a name="bmcprocessor"/>

### BMC Processor

BMC processor controls the PSU, board voltage rails, fan speed, and
other GPIO on the board. For this release, there is nothing to configure
on the BMC. Everything, including temperature and fan speed, is
automated.

<a name="intelprocessor"/>

### Intel Processor

After power up, the RS-232 serial console defaults to Intel CPU
console. The prompt is the Linux prompt. Everything needed for using,
configuring, and monitoring the unit can be done from here.

It is possible to switch the RS-232 serial console to between the x86 and
the BMC consoles. This is described below in a section titled
[ Getting to the BMC Console](#gettingtothebmcconsole).

<a name="linux"/>

### Linux

Linux is the operating system installed on the PSW-3001-32C. The unit is
pre-loaded
with stock Debian Jessie and kernel version 4.13.0. The admin account is
“root”; password “platina”. This password should be changed before bringing
the device up on the network.

Standard Linux commands and utilities can generally be expected to behave as
with any Linux distribution. Enhancements to certain functionality is
documented elsewhere within this guide.

By default eth0 is the RJ45 Management Ethernet port on the front panel.

<a name="platinagoesservice"/>

### Platina GOES Service

GOES, the core Platina service, is a user space application that runs on Linux.
GOES is pre-installed on each device.  Starting with goes v2.0, goes is a debian package.  To manually install GOES (i.e. SW
upgrade/downgrade, re-install), make sure

    https://platina.io/goes/debian stretch main

is in the /etc/apt source list.

Enter the following command:

    sudo apt-get install goes-platina-mk1

Once installed, GOES will startup automatically on reboot going forward.

You can verify GOES is running properly by entering

    goes status

which gives the following output on success:

    GOES status
    ======================
      Mode            - XETH
      Check PCI       - OK
      Check daemons   - OK
      Check redis     - OK
      Check fe1       - OK

GOES a systemd application, so you can also use the systemctl command to check the status, start, stop, enable, or disable the application.

      sudo systemctl stop goes-platina-mk1
      sudo systemctl start goes-platina-mk1
      sudo systemctl enable goes-platina-mk1
      sudo systemctl disable goes-platina-mk1

Each stop/start will reset all ASIC configuration/memory and reinitialize the ASIC. This may result in a short disruption to network forwarding.

<a name="adminprivilege"/>

## Admin Privilege

GOES binary is install in /sbin/goes-platina-mk1 when the debina package is installed, with /sbin/goes as an alternative.  Admin privilege is required to access it.

<a name="redisdatabaseinterface"/>

## Configuring The Platina Cluster Head
Platina Cluster Head is a Linux server running Debian OS.  All the ASIC interfaces, funcationalities, and stats supported by GOES are avaible to configure and monitor via standard Linus tools and commands such as ethtool and iproute2.  All front panel interfaces appear in Linux as ethernet interfaces with xeth* prefix, and can be used like typical Linux interfaces as if they were part of a NIC on a server.  These interface will be often referred to as xeth interface through out this document for short.

### Configuring the Breakout
The Platina Cluster Head has 32 front-panel QSFP ports, each of which can be broken out into 1, 2, or 4 subports.  By default they are configured as single 40GE/100GE interface each.  These interfaces are created by a platina kernel module called xeth.  The breakout configurations are persisted in

    /etc/modprobe.d/goes-platina-mk1-modprobe.conf

with the default:

options xeth platina-mk1_provision=1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1

To breakout an QSFP port ot 2x40GE/50GE or 4x1GE/10GE/20GE/25GE, change the "1" to a "2" or "4" for the corresponding interface (the array is ordered from port1 to port32).  After the xeth provision is changed, do

    sudo systemctl stop goes-platina-mk1
    sudo rmmod xeth
    sudo modprobe xeth
    sudo systemctl start goes-platina-mk1
    sudo update-initramfs -u

for the new configuration to take effect and persist across reboots.

When a front panel port is configured as a single 40GE/100GE interface, they are named in Linux as xeth1, xeth2, ..., or xeth32.  When an interface is broken out into 2 or 4 sub-ports, suffix are added to to indicate the subport.  For example if port2 is broken out into 2x40GE/50GE, then they will show in Linux as xeth2-1 and xeth2-2.  Similarly if port2 is broken out into 4x1GE/10GE/20GE/25GE they will show in Linux as xeth2-1, xeth2-2, xeth2-3, xeth2-4.

### Configuring Interfaces
A front-panel, or xeth, interface is like any other Linux ethernet interface.  Use iproute2, ifconfig, or any other standard Linux method to set the admin state, addresses, mtu, etc.  These xeth interface configuration can also be persisted in standard ifupdown network manager in /etc/network/

### Configuring Speed/Autoneg with Ethtool
Speed/autoneg of xeth interfaces can be configured using ethtool.  For example to configure xeth1 to 40GE fixed speed:

    sudo ethtool -s xeth1 speed 40000 autoneg off

To configure xeth1 to autoneg:

    sudo ethtool -s xeth1 speed autoneg on

The supported speeds are:
#### Single port (e.g. xeth1)
```
autoneg (auto negotiate between 40GE and 100GE)
40GE
100GE
```

#### 2-sub-port (e.g. xeth1-1, xeth1-2)
```
40GE
50GE
```
Note that the 2 sub-ports share the same PLL (phase-lock-loop).  Changing xeth1-1 effectively changes xeth1-2 as well; changing xeth1-2 without first changing xeth1-1 is not allow, and xeth1-2 will be set to the same speed as xeth1-1.

#### 3-sub-port
Not supported

#### 4-sub-port (e.g. xeth1-1, xeth1-2, xeth1-3, xeth1-4)
```
autoneg
10GE
20GE
25GE
```
Autonegotiation negotiates to 10GE only if the other end of the link supports autoneg as well.

Note that the 4 sub-ports share the same PLL (phase-lock-loop).  Changing xeth1-1 may effectively change the speed of the other sub-ports as well; changing speeds on sub-port that do not match PLL of first sub-port (e.g. xeth1-1) is not allow, and a valid speed (based on the PLL of the first sub-port) will be configured instead.  Here are examples of valid configurations:
```
Example 1:
xeth1-1: 10GE/20GE/autoneg
xeth1-2: 10GE/20GE/autoneg
xeth1-3: 10GE/20GE/autoneg
xeth1-4: 10GE/20GE/autoneg

Example 2:
xeth1-1: 25GE
xeth1-2: 25GE
xeth1-1: 25GE
xeth1-2: 25GE
```
### Configuring Media Type with Ethtool
The xeth interfaces support 2 media types, copper for copper direct attach QSFP cable, and optics.  The media can be configured using ethtool, "tp" for copper and "fibre" for fiber.  Eventhough techncially copper QSFP are not twisted pair, it is the closest configuration in standard ethtool to represent copper.  Examples:
```
sudo ethtool -s xeth1 port tp
sudo ethtool -s xeth1 port fibre
```

### Configuring FEC with Ethtool
The xeth interface supports clause74 or clause91 FEC depending on the speed of the interface.  The FEC enconding can be configured using ethtool.  Examples:
```
sudo ethtool -s --set-fec xeth1 encoding auto
sudo ethtool -s --set-fec xeth1 encoding rs
sudo ethtool -s --set-fec xeth1 encoding baser
sudo ethtool -s --set-fec xeth1 encoding off
```
"off" means no FEC.

"rs" is reed solomon encoding per clause91, and is really applicable for 100GE standards like copper-DAC cable and 100GE-SR4.

"baser" is clause74 encoding, applicable to some 50GE, 40GE, and 10GE standards.

"auto" will pick clause91 for if the interface is configured for 100GE, clause74 if the interface is configured for 50GE/40GE/10GE, and none if the interface is configured for 1GE.

### Interface Stats
Simple interface counter stats are available in Linux like any other Linux interfaces.  They are available, for example, using iproute2 commands:
```
ip -s link show xeth1
```
Detailed interfaces stats like packet counters, drop counters, error counters, buffer counters, etc. are available via ethtool.  Example:
```
sudo ethtool -S xeth1
```
### QSFP stats with Ethtool
QSFP modules are mapped into Linux devices directly.  To get QSFP module stats like tx/rx optical power, module type, etc of a QSFP port, say xeth1-1:
```
sudo ethool -m xeth1
```
In case breakout is configured on a front panel port for 2 or more sub-ports, use the lowest numbered sub-ports.  Example:
```
sudo ethtool -m xeth1-1
```

## Routing
By default every interface of the Platina Cluster Head is a routed interface.  All routes in Linux kernel are automatically mapped to the ASIC, regardless of whether the routes are added to the kernel statically or from routing protocol.  The recommended and supported routing protocol to use is the open-source FRR (Free Range Routing).  Is is not installed on the unit by default, but can be installed as a debian package from the office FRR download sites.

### IPV4/IPV6 Dual Stack
In GOES v2.0 and above, both IPv4 and IPv6 are supported.  The TCAM allocation between IPv4 and IPv6 is dynamically allocated base on use.

### Route Table Size and Software Forwarding
The physical TCAM size in the ASIC is equivalent of 4k IPv4 routes.  Because it is dynamically alloated between IPv4 and IPv6, the example number of routes that are stored in TCAM varies depending on usage.  If the TCAM size is exceed, routes are cached in memory and Platina Cluster Head will automatically software forward those routes.  Once the number of routes falls within the hardware limitation, the cached routes will automatically get installed into ASIC.

## Redis Database/Interface

GOES includes a Redis server daemon. All the GOES managed configuration and stats available from ethtool are also available in redis for pub/sub.  The stats from redis is namespace agnostic so that all interfaces, regardless of what network namespaces they are in, are available from same redis database.  Furthermore, therea some stats, such as ASIC temperature, MFG eeprom contents, etc., that are available only in from redis. The GOES Redis server is a standard Redis server listening on port 6379 of the loopback interface and eth0. The database can be accessed remotely anywhere via standard Redis-client and Redis-cli using the management IP address.

To invoke Redis commands directly from the Linux CLI, precede the Redis
command with “goes”, otherwise standard Redis command format should be
used from a Redis client. In this guide, the command examples will
assume the user is invoking from the device’s Linux CLI.

To see a list of all parameters in this Redis database, enter:

From Linux CLI:

    goes hgetall platina-mk1

From a Redis client:

    hgetall platina-mk1

“platina-mk1” is the hash for which all of the unit’s configurations and
stats are stored under. The field/value associated with platina-mk1
appear in the output as field:value.

You can view just a particular set of fields using hget. For example to
get all configuration/stats associated with front panel port xeth1,
enter:

    goes hget platina-mk1 xeth1

Redis database is updated every 5 seconds by default for stats counters.

Included in the GOES Redis interface is a convenience command hdelta.
hdelta returns only the non-zero differences from the last Redis update
and includes rate calculation if applicable. hdelta runs continuously
until stopped by ctrl-c. hdelta is not a standard Redis command and must
be invoked with the following command via CLI.

    goes hdelta

Since the commands above are invoked at the standard Linux command line
prompt, ‘grep’ or other Linux tools can be used to further filter the
output.

<a name="appendix1redisfieldsguide"/>

## Appendix 1: Redis Fields Guide

The examples in the appendix show standard Redis commands. When directly
on the device’s Linux CLI, add “goes” in front of the Redis command.

From Redis-client:

    hgetall platina-mk1

From device Linux prompt:

    goes hgetall platina-mk1

To get multiple field names that contain a specific string, use hget
platina-mk1 &lt;string&gt;, for example:

    goes hget platina-mk1 xeth1

When using redis-cli, it is recommended to connect using the --raw
parameter so that newline characters between the multiple fields are
parsed properly. For example:

    redis-cli --raw -h <ipv4_address> hget platina-mk1 xeth1

<a name="fieldsthatcanbesetinplatinasredis"/>

### Physical link state (as reported by switch ASIC)

vnet.\[interface\].link indicates the physical link state as reported by
the switch ASIC. The value is “true” if link is up, “false” if link is
down.

Example:

    goes hget platina-mk1 vnet.xeth3.link
    false

### Linux Packet/Byte counters

The Linux interface counter (e.g. via ip link or ifconfig) counts
packets that have been sent/received on each ASIC interface.
To get the detailed ASIC level interface
counters, use vnet.\[interface\].port redis commands instead.

    ip -s link show xeth12

    16: xeth12@eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 50:18:4c:00:11:87 brd ff:ff:ff:ff:ff:ff
    RX: bytes packets errors dropped overrun mcast
    1120240923480 1054840793 0 0 0 10
    TX: bytes packets errors dropped carrier collsns
    1966 15 0 0 0 0


### Port Counters

vnet.\[interface\].port… are counters that reflect the interface
counters as reported by the switch ASIC. These counters count the number
of packets/bytes that are coming in or going out of the switch ASIC,
as well as counters for various types of recognized packet types and any errors/drops encountered for
the corresponding front panel ports.

Example: (assume launching from devices local prompt; otherwise hget
each field 1 at a time)

    goes hget platina-mk1 vnet.xeth9.port

    vnet.xeth9.port-rx-1024-to-1518-byte-packets: 1445258343
    vnet.xeth9.port-rx-128-to-255-byte-packets: 0
    vnet.xeth9.port-rx-1519-to-1522-byte-vlan-packets: 0
    vnet.xeth9.port-rx-1519-to-2047-byte-packets: 0
    vnet.xeth9.port-rx-1tag-vlan-packets: 0
    ...

### Interface MMU Counters

vnet.\[interface\].mmu… are counters that reflect drops at the switch
ASICs memory management unit (MMU). This is applicable to the Broadcom
Tomahawk switch ASIC that employs the MMU to manage/switch traffic
between 4 packet processing pipelines. The \[interface\] is the egress
port, and the queues are queues associated with that port. For example,
if “vnet.xeth9.mmu-multicast-tx-cos1-drop-packets” is non-zero, that
means packets destined for xeth9 is dropping at the MMU’s multicast,
priority 1 queue.

Example:

    goes hget platina-mk1 vnet.xeth9.mmu

    vnet.xeth9.mmu-multicast-tx-cos0-drop-bytes: 0
    vnet.xeth9.mmu-multicast-tx-cos0-drop-packets: 0
    vnet.xeth9.mmu-multicast-tx-cos1-drop-bytes: 0
    vnet.xeth9.mmu-multicast-tx-cos1-drop-packets: 0
    ...

### Interface Pipe Counters

vnet.\[interface\].rx-pipe… and vnet.\[interface\].tx-pipe… are counters
that reflect counters at the switch ASICs packet processing pipelines.
The rx-pipe… reflect counters for the ingress pipeline, and tx-pipe…
reflect counters for the egress pipeline. The \[interface\] is the
egress port, and the queues are queues associated with that port. For
example “vnet.xeth9.tx-pipe-multicast-queue-cos0-packets” indicates
multicast packet counters on queue 0

Example:

    goes hget platina-mk1 vnet.xeth9.rx-pipe

    vnet.xeth9.rx-pipe-debug-6: 0
    vnet.xeth9.rx-pipe-debug-7: 0
    vnet.xeth9.rx-pipe-debug-8: 0
    vnet.xeth9.rx-pipe-dst-discard-drops: 0
    vnet.xeth9.rx-pipe-ecn-counter: 0
    ...

<a name="fe1counters"/>

### fe1 counters

fe1 counters captures counters not associated with any front panel
interface. Examples are loopback port and cpu ports as seen back the
switch ASIC.

Example:

    goes hget platina-mk1 fe1|grep cos0

    vnet.fe1-cpu.bst-tx-queue-cos0-count: 0
    vnet.fe1-cpu.mmu-multicast-tx-cos0-drop-bytes: 0
    vnet.fe1-cpu.mmu-multicast-tx-cos0-drop-packets: 0
    vnet.fe1-cpu.mmu-unicast-tx-cos0-drop-bytes: 0
    vnet.fe1-cpu.mmu-unicast-tx-cos0-drop-packets: 0
    ...

<a name="eth0stats"/>

### Eth0 stats

Eth0 is the RJ45 management ethernet port that goes straight from the
CPU to/from the front panel RJ45. All the eth0 stats are available in
Linux.

<a name="eepromcontents"/>

### EEPROM contents

These Redis fields show the content of the EEPROM that includes
manufacturing information on the specific hardware unit such as the part
number and serial number.

Example:

    goes hget platina eeprom

    eeprom.BaseEthernetAddress: 6c:ec:5a:07:cb:54
    eeprom.CountryCode: 86
    eeprom.Crc: 0x4bc3c14e
    eeprom.DeviceVersion: 0x02
    eeprom.DiagVersion: DIAG_TOR1_1.1.1
    ...

<a name="appendix2bmcredis"/>

## Appendix 2: BMC Redis

The BMC runs a separate Redis server that provides configuration and
status of the hardware platform including power supplies, fan trays, and
environmental monitoring.

Accessing the BMC redis server should be done via Redis client. For
convenience, the redis-tools package is pre-installed in the device’s
Linux (“sudo apt-get install redis-tools”) and includes the redis-cli
command that can be used to access the BMC redis from the device’s Linux
CLI.

The BMC Redis server listens on port 6379 of the BMC’s eth0 IPv4 address
and IPv6 link local address.

<a name="connectingviaipv4"/>

### Connecting via IPv4

By default the BMC eth0 IPv4 address is 192.168.101.100. To connect from
the device’s Linux CLI:

    root@platina:~# redis-cli -h 192.168.101.100
    192.168.101.100:6379> hget platina machine*
    "platina-mk1-bmc"

<a name="connectingviaipv6linklocal"/>

### Connecting via IPv6 Link Local

The BMC eth0 IPv6 link local address can be directly translated from the
BMC eth0 MAC address. The BMC eth0 MAC address is simply the base MAC
address of the system which can be retrieved from the device’s Linux
CLI:

    root@platina:~# goes hget platina eeprom.BaseEthernetAddress
    50:18:4c:00:13:04

Convert *50:18:4c:00:13:04* MAC address to IPv6 link local:
fe80::5218:4cff:fe00:1304 and connect to BMC redis:

    root@platina:~# redis-cli -h fe80::5218:4cff:fe00:1304%eth0
    [fe80::5218:4cff:fe00:1304%eth0]:6379> hget platina machine*
    "platina-mk1-bmc"

<a name="notablebmcredisfields"/>

### Notable BMC Redis Fields

Temperature status

    redis-cli --raw -h fe80::5218:4cff:fe00:1304%eth0 hget platina temp

    bmc.temperature.units.C: 37.01
    hwmon.front.temp.units.C: 49.000
    hwmon.rear.temp.units.C: 54.000
    psu1.temp1.units.C: 33.375
    psu1.temp2.units.C: 37.812

Fan and PSU status

    redis-cli --raw -h fe80::5218:4cff:fe00:1304%eth0 hget platina status

    fan_tray.1.status: ok.front-&gt;back
    fan_tray.2.status: ok.front-&gt;back
    fan_tray.3.status: ok.front-&gt;back
    fan_tray.4.status: ok.front-&gt;back
    psu1.status: powered_on
    psu2.status: not_installed

Fan Speed

    redis-cli --raw -h fe80::5218:4cff:fe00:1304%eth0 hget platina fan_tray

    fan_tray.1.1.speed.units.rpm: 7031
    fan_tray.1.2.speed.units.rpm: 7031
    fan_tray.1.status: ok.front-&gt;back
    fan_tray.2.1.speed.units.rpm: 7031
    fan_tray.2.2.speed.units.rpm: 6490
    fan_tray.2.status: ok.front-&gt;back
    fan_tray.3.1.speed.units.rpm: 7031
    fan_tray.3.2.speed.units.rpm: 7031
    fan_tray.3.status: ok.front-&gt;back
    fan_tray.4.1.speed.units.rpm: 7031
    fan_tray.4.2.speed.units.rpm: 6490
    fan_tray.4.status: ok.front-&gt;back
    fan_tray.duty: 0x4d
    fan_tray.speed: auto

<a name="psuinformation"/>

### PSU Information

    redis-cli --raw -h fe80::5218:4cff:fe00:1304%eth0 hget platina psu

    psu1.admin.state: enabled
    psu1.eeprom:
    01000000010900f5010819c54757202020cb47572d4352505335353020ca58585858585...
    psu1.fan_speed.units.rpm: 4020
    psu1.i_out.units.A: 10.688
    psu1.mfg_id: Great Wall
    psu1.mfg_model: CRPS550
    psu1.p_in.units.W: 141.000
    psu1.p_out.units.W: 129.000
    psu1.status: powered_on
    psu1.temp1.units.C: 33.375
    psu1.temp2.units.C: 37.812
    psu1.v_in.units.V: 117.000
    psu1.v_out.units.V: 12.047
    psu2.admin.state: enabled
    psu2.status: not_installed

<a name="powermonitorinformation"/>

### Power Monitor Information

    redis-cli --raw -h fe80::5218:4cff:fe00:1304%eth0 hget platina vmon

    vmon.1v0.tha.units.V: 1.041
    vmon.1v0.thc.units.V: 1.014
    vmon.1v2.ethx.units.V: 1.187
    vmon.1v25.sys.units.V: 1.24
    vmon.1v8.sys.units.V: 1.805
    vmon.3v3.bmc.units.V: 3.28
    vmon.3v3.sb.units.V: 3.344
    vmon.3v3.sys.units.V: 3.298
    vmon.3v8.bmc.units.V: 3.826
    vmon.5v.sb.units.V: 4.926
    vmon.poweroff.events:
    1970-01-01T23:30:34Z.1970-01-01T23:32:28Z.1970-01-01T23:40:17Z.1970-01-01T23:50:54Z.1970-01-01T23:52:04Z

<a name="softwareandfirmwareupdates"/>

# Software and Firmware Updates

### Updating Cluster Head Platina Debian Package
Platina software running on the Cluster Head includes the GOES binary is userspace, xeth kernel driver, and GOES-boot which takes the place of typcial BIOS.  They are all packaged into a debian package so that dependencies and configuration are automaticallyd one on install.

Make sure /etc/apt source list includes
```
https://platina.io/goes/debian stretch main
```
Then:
```
sudo apt-get update
sudo apt-get install platina-mk1-release
```
The package install will update the debian kernel (which include any required kernel module like xeth), GOES-boot, and GOES.

#### Protip:
After platina-mk1-release install completes, goes-boot is now written into the flash.  It will take effect on next reboot.
#### Protip:
After platina-mk1-release install completes, kernel version is upated and will be installed on next reboot.
#### Protip:
If upgrading from goes v1.2.x to goes v2.x run additionally after the above:
```
sudo apt-get dist-upgrade
```
This is because of major changes in dependencies between v1.2.x and v2.x.x.  Once this is done once, subsequent updates/upgrades of platina-mk1-release do not need the "dist-upgrade" command again.

### Upgrading Individual Packages
The package platina-mk1-release will install any dependent packages.  If needed the packages can be installed individually as well.  Most common is the GOES package running in user space.

Make sure /etc/apt source list includes
```
https://platina.io/goes/debian stretch main
```
Then:
```
sudo apt-get update
sudo apt-get install goes-platina-mk1
```

### Updating the BMC Firmware

---
You must upgrade the BMC using the GOES shell on the BMC console. It cannot be upgraded using the system GOES shell. For instructions on how to connect to the BMC console, see the section below titled _Getting to the BMC Console_.

From BMC console CLI, execute the command:

    upgrade -v LATEST -s downloads.platinasystems.com

This will automatically retrieve the upgrade file (platina-mk1-bmc.zip) from http://downloads.platinasystems.com/LATEST/, perform the update, then reboot the BMC to complete the upgrade. This BMC reboot only impacts the BMC and not the running system.

- _LATEST_ above may be replaced by any version control string (e.g. 'v0.2').
- _downloads.platinasystems.com_ above may be replaced with any reachable HTTP server hostname or IP address. For example: `upgrade -v v0.2 -s 192.168.101.127` will retrieve the URL http://192.168.101.127/v0.2/platina-mk1-bmc.zip.
- If the -s option is not specified, the default URL (http://downloads.platinasystems.com/) is used to retrieve the update file.
- To see a list of software revisions available through http://downloads.platinasystems.com/ execute the GOES command `upgrade -l`

## Additional Information

### Download the flash ROM and Coreboot images (if /usr/local/sbin/flashrom doesn't already exist)

To retrieve the flash ROM, execute the following Linux commands:

```
sudo bash
cd ~/
wget http://downloads.platinasystems.com/tools/flashrom
wget http://downloads.platinasystems.com/tools/platina-mk1.xml
chmod 655 flashrom
mv flashrom /usr/local/sbin/flashrom
mkdir -p /usr/local/share/flashrom/layouts
mv platina-mk1.xml /usr/local/share/flashrom/layouts

```

### Getting to the BMC Console

The RS-232 port on the front of the Cluster Head is used to drive the system console of the Platina Cluster Head _and_ the console of the Baseboard Management Controller (BMC). This section demonstrates how to toggle between the BMC console and the system console.

To switch to BMC console:

- At the system console (Linux) prompt, execute the command `sudo goes toggle`
- Hit return to redisplay the prompt
- The BMC console prompt should be displayed and looks like this:

    203.0.113.75>


To switch back to x86 console:

- At the BMC console prompt, execute the `toggle` GOES command.
- Hit return to display the Linux prompt on the system console

#### Configuring static IP for the BMC processer

The BMC processor has its own management interface that can be assigned a static IP address.  By default only the IPv6 link local address is assigned to it.
To assign a static IP address to the BMC processor, enter the following commands at the BMC console

ipcfg -ip [ipaddress]::[gateway]:[mask]::eth0:on
reboot
Example:
```
ipcfg -ip 172.17.3.68::172.17.2.1:255.255.254.0::eth0:on
reboot
```
The reboot only reboots the BMC processor, and takes approximately 5 seconds.  It will not impact traffic or activity on the main x86 processor or ASIC.

# Support

Any questions or to report new issues, please email

[*support@platinasystems.com*](mailto:support@platinasystems.com)
