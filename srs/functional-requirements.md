# Functional Requirements

_<font color="gray">
&lt;Itemize the specific functional requirements associated with this product. These are the software capabilities that must be implemented for the user to carry out the product’s services or to perform a use case. Describe how the product should respond to anticipated error conditions and to invalid inputs and actions. Uniquely label each functional requirement, such as REQ-1, REQ-2.&gt;
</font>_


## REQ-1 Configurable MODBUS Framework

### REQ-1.1
Configurable MODBUS TCP/RTU master.

### REQ-1.2
Minimum scan interval is 1 sec.

### REQ-1.3
Provide point-slope and point-to-point scaling formula.

### REQ-1.4
Accept pre-configured MODBUS equipment template.

### REQ-1.5
Built-in MOXA ioLogik E12XX/R12xx MODBUS remote I/O.

### REQ-1.6
Test equipment template via actual TCP/RTU equipment while editing it.

### REQ-1.7
Test actual equipment while editing it.

### REQ-1.8
Provide **last update time** and **status** for each equipment.


## REQ-2 Data Logging

### REQ-2.1
Support MODBUS equipment-tag data as the logging data source.

### REQ-2.2.1
Each profile should be able to configure its:
   - Tag List
   - Maximum Storage Size
   - Upload URL
   - Upload Schedule
   - File Format

### REQ-2.2.2
Besides **MODBUS equipment-tag data**, log file should contain a **date/time**
field filled with tag-reading-time(not storing-time).

### REQ-2.2.3
Logging system should start logging once a profile is configured.

### REQ-2.2.4
**Maximum Storage Size** for a profile shall have a minimum as **10MB**.

### REQ-2.2.5
Whenever the storage size exceeds limit, the oldest log-file would be deleted.(FIFO)

### REQ-2.2.6
Both **IP** and **hostname** should be acceptable for upload URL.

### REQ-2.2.7
Minimum interval for upload schedule is **1 hour** (by the hour) and **offset**
with **minutes** should be provided.

### REQ-2.2.8
Support both **XML**, **CSV** and **JSON** as log file format.

### REQ-2.2.9
Log files are compressed in *.gz format.
Log file compression should be able to be enabled or disabled.

### REQ-2.2.10
Provide an **Upload Now** method to upload data log on-demand.

### REQ-2.3
Log files are segmented at 0 minute every hour or by a system-decided size limit.

### REQ-2.4
Filename will be formatted automatically by date/time with the format:
**yyyyMMddhhmm.log**, with date/time at the time of log file creation.

### REQ-2.5
Upload retry is set to **3** times, if all fail, system will wait for
**next schedule**.

### REQ-2.6
Log files shall be received by a standard **HTTP** server with **gzip**
decompression capability.

### REQ-2.7
Support **Log on Change**.

Enable/disable **Log on Change** by Tag.
Users can either enable or disable "Log on Change" of a Tag in a Log Profile
without effecting the configuration of the same Tag in other Log Profiles.

After a Tag is read, only Tags with their value changed are written to log
files.
For example,

All disabled:

```
at,di0@E1210,di1@E1210,di2@E1210
"2015-10-19T03:08:02.004Z","1","1","1"
"2015-10-19T03:08:03.004Z","0","0","1"
"2015-10-19T03:08:04.004Z","0","0","0"
"2015-10-19T03:08:05.004Z","0","0","0"
```

di0 and di1 enabled, di2 disabled:

```
at,di0@E1210,di1@E1210,di2@E1210
"2015-10-19T03:08:02.004Z","1","1","1"
"2015-10-19T03:08:03.004Z","0","0","1"
"2015-10-19T03:08:04.004Z",,,"0"
"2015-10-19T03:08:05.004Z",,,"0"
```

## REQ-3 Device Management

### REQ-3.1
System Date/Time should be able to be configured.

#### REQ-3.1.1
System Date/time can be set **manually**.

#### REQ-3.1.2
System Date/time can be updated via a **NTP** client.

#### REQ-3.1.3
Date/time can be set into system **RTC**.

#### REQ-3.1.4
**Time Zone** should be able to update.


### REQ-3.2
System should be upgraded via a firmware file.

#### ~~REQ-3.2.1~~
~~Firmware can be upgraded via **USB storage** during booting.~~

#### ~~REQ-3.2.2~~
~~Firmware can be upgraded via **ssh** console (using sftp to upload firmware).~~

#### REQ-3.2.3
Firmware can be upgraded via **web** page by uploading a firmware file.
   - ~~Limitation: If kernel was upgraded, *reset to factory default* won't reset the kernel version.~~

#### REQ-3.2.4
The *red diagnosis LED will off*, *yellow and green diagnosis LEDs will blink* while upgrading.

#### REQ-3.2.5
Firmware’s file name should be **UC-8100-LX-CG_V#.#_Build_YYMMDDhhmm.frm**.

#### ~~REQ-3.2.6~~
~~File format of USB storage should be **ext3**, **ext4**, or **fat32**.~~

#### REQ-3.2.7
System storage should keep at least 500MB for firmware upgrading.

#### REQ-3.2.8
A firmware includes many packages, only packages with higher version are updated.

### REQ-3.3
CG can be rebooted via CG's Web.

### REQ-3.4
CG settings can be imported/exported from/to a file.

#### REQ-3.4.1
Equipment template should be able to export by selection.

#### REQ-3.4.2
Equipment templates should support multiple import.

On template name conflict, users can either overwrite or ignore the conflicting template.

#### REQ-3.4.3
Each configuration in *Settings* page should be able to be imported individually.

#### REQ-3.4.4
Support import/export for modbus framework to export equipment templates, equipment settings, and log profile settings.
   - Equipment settings and log profile settings cannot be imported without equipment templates.


### REQ-3.5
Check and validate all MOXA Ethernet MACs for software lock (via CG profile)

### REQ-3.6
Ethernet interfaces could be configured.

#### REQ-3.6.1
The type of LAN1 is WAN and LAN2 is LAN.

#### REQ-3.6.2
Default route is set to LAN1 while cellular connection is down.
Once cellular connection is up, the default route will be replaced by the address given by cellular-operator.

#### REQ-3.6.3
LAN1 could be set to **static IP** (IP, netmask, gateway, DNS1, and DNS2) or **DHCP client**.

#### REQ-3.6.4
LAN2 could be set to **static IP** (IP and netmask) or **DHCP client**.

#### REQ-3.6.5
~~In *Cellular Router mode*, ~~**DHCP server** could be enabled and configured on interface with *LAN* type.
Either DHCP client or DHCP server could be configured, but not at the same time.


### REQ-3.7
Cellular interfaces should be configurable.

#### REQ-3.7.1
**APN** and **PIN code** is able to be configurable.

#### REQ-3.7.2
Reconnection mechanism must be supported.

#### REQ-3.7.3
**Keepalive**, **ping target** and **ping interval** should be configurable.
  - default target: 8.8.8.8
  - default interval: 1 minute

#### REQ-3.7.4
Cellular information such as **RSSI**, **LAC**, **cell ID** should be able to log **every minute** and the logs should be kept for **7 days**.
  - ~~information should be logged into syslog~~
  - ~~default disabled~~
  - ~~log could be downloaded~~

#### ~~REQ-3.7.5~~
~~Log for cellular connection information and keeplive/reconnection should be able to download~~

#### REQ-3.7.6
**Connection status**, **APN**, **Operator name**, **signal**, **ICC-ID**, ~~**phone number**~~ and station information of ~~, **BSIC**, **TCH**, and~~ **service type** (3G or 4G) should be shown if SIM inserted and unlocked.
  - BSID is only for GSM
  - TCH not supports

#### REQ-3.7.7
**IP**, **DNS**, and **default route** should be shown while connected.

#### REQ-3.7.8
Module information such as **IMEI** should be shown if available.

#### REQ-3.7.9
The **network traffic** (byte sent / rcvd) should be shown.


### REQ-3.8
DNS could be overridden by an **alternative primary and secondary DNS** instead of WAN's configuration.

### REQ-3.9
Any system configuration should be restored to Factory Default after performing reset-to-factory.

### REQ-3.10
Logging system should be provided for diagnosis; which allows user to enable or disable.

### REQ-3.11
**System logs** should be able to download for diagnosis.

#### REQ-3.11.1
Each boot and reboot should be traceable from system logs.

#### REQ-3.11.2
Logs should be kept for **7 days**.


### REQ-3.12
Password for web account must able to be modified.

### REQ-3.13
SSH server should be able to be enabled or disabled; enabled by default.

### REQ-3.14
Mode for *Modbus Framework* or *Cellular Router* should be and only could be selectable once, at first boot.

### REQ-3.15
Web could be accessed via LAN by default; an option should be provided to enable WAN accessibility.

### REQ-3.16
Able to view disk usage of secondary SD card on *UC-8112-LX-CG*.

### REQ-3.17
Basic system information such as **software version**, **uptime**, and **disk usage** should be provided.

### REQ-3.18
**Hostname** should be able to modified.

### REQ-3.19
The **mode** of serial port 1 and 2 should be able to configured to **RS232**, **RS485-2W**, or **RS422/RS485-4W**.


## REQ-4 Cellular Router

### REQ-4.1
Port forwarding must be provided; support maximum **10** entries.

### REQ-4.2
Each entry of port forwarding should support **port range**, **protocol** of UDP, TCP or both and **IP address**.

### REQ-4.3
**NAT** enabled by default with WAN as outgoing interface.

### REQ-4.4
Support cellular (client with **UDP** or **TCP**) to ethernet (LAN with **UDP** or **TCP**).

In this phase only following scenario is supported:
- cellular (client UDP/TCP) <-> [uc8100 server UDP/TCP - uc8100 client UDP/TCP] <-> ethernet server LAN

### REQ-4.5
Support cellular (client with **UDP** or **TCP**) to serial.

In this phase only following scenario is supported:
- cellular (client UDP/TCP) <-> [uc8100 server UDP/TCP] <-> serial

### REQ-4.6
**Baud rate**, **parity**, **stopbits**, and **databits** of serial interface for _cellular to serial_ should be able to be configured.

### REQ-4.7
Provide 2 sets of relay settings (cellular to ethernet / cellular to serial).

### REQ-4.8
Provide **10** entries for **Static NAT** with WAN as outgoing interface.

### REQ-4.9
Each entry of static NAT should support **internal IP address**, **port range**, and **protocol** of UDP, TCP or both.
