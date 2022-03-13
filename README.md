# unix_collector

A shell script for basic forensic collection of various artefacts from UNIX systems.

```unix_collector``` is a script that runs on Unix systems and attempts to collect various artefacts which could be analysed in attempt to identify potential system compromise. ```unix_collector``` is written as a single shell script so it can be easily uploaded and run (as opposed to un-tarred, compiled and installed). It can run either as a normal user or as root. It does a better job when running as root because it can read more files of course.

# Available platforms

* Sun Solaris
* Linux
* IBM AIX
* HPUX
* MacOS
* Probably others as well.

# Script Activities

* Enumerate basic host information such as kernel version, processes, hostname and save details in output directory.
* Enumerate network information and save details in output directory.
* Enumerate patch and installed software information and save details in output directory.
* Enumerate process list and other process information and save details in output directory.
* Hash files in various folders such as /home/ /opt/ /usr/ and save details in output directory.
* Hash files which are marked as SGID or SUID and save details in output directory.
* Copy various files such as cron job, plist or other files into output directory.
* Copy SUID/SGID binaries into output directory.
* Copy system logs (i.e /var/log or /var/adm/) into output directory.
* TAR entire output directory and use hostname as file name with current date.

# Requirements

* Enough space on the disk so logs and other files can be copied into single location (alternatively run from mounted disk or network partition).
* sh

# Examples 

Execute ```unix_collector``` without specifying any operating system version (script will guess OS type):

```chmod +x ./unix_collector.sh && ./unix_collector.sh```

Execute ```unix_collector``` on AIX while specifying platform:

```chmod +x ./unix_collector.sh && ./unix_collector.sh --platform=aix```

Execute ```unix_collector``` on MacOS while specifying platform:

```chmod +x ./unix_collector.sh && ./unix_collector.sh --platform=mac```

# Sample Output
```
PLATFORM: GNU/Linux

BASIC INFORMATION [0%  ]:
  > UNIX Collector
  > UNIX Collector Date
  > UNIX Collector User
  > UNIX Collector Platform
GENERAL INFORMATION [15%  ]:
  > Hostname
  > Kernel
  > Version
  > Release
  > Processor
  > Full OS Info
  > Process list
  > Cron scheduler
  > Kernel Modules
  > At scheduler
  > Kernel settings
  > Environment
  > ulimit
  > Auditd
INSTALLED SOFTWARE AND PATCHES [25% ]:
  > Installed software (this could take a few mins)
  > Installed patches
  > Compiler tools
LOG FILE COLLECTION [50% ]:
  > Copying logs
SUID/SGID SEARCH [60% ]:
  > Finding all SUID/SGID binaries
 HASH BINARIES [65% ]:
  > Hashing all SUID/SGID binaries
  > Hashing all HOME dirs
  > Hashing all /bin /sbin /usr/ /opt/ /tmp/ dirs
NETWORK INFORMATION [90% ]:
  > Interface configuration
  > IP addr
  > IP forwarding
  > Routing
  > Netstat
  > ARP cache
  > Hosts
  > DNS
  > TCP wrappers
  > RPC
  > IP Tables
  > IP Tables (IPv6)
FINISHING [100%]:
  > Removing empty files
  > Creating TAR file
  > Removing temporary directory
```
