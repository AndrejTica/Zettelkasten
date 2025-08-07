---
date: 2025-05-10
tags:
  - linux
---
Mirros are simply servers that host packages. The purpose is to:

- Distribute load
- Increase download speed
- Increase availability

## Reflector
Reflector is a arch linux based tool for managing mirrors. 
Its job is to find the best mirrors automatically based on:
- geographic location
- response time
- if the packages are synched (up to date)

```
sudo reflector --country Germany,Austria --latest 20 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
```

this command will:
- select mirrors from austria
- use 20 most recently updated ones
- use HTTPS
- sort them by speed
- save them to the system

Use reflector because otherwise the mirrors might become outdated or slow.
## Mirrors location

On arch linux the mirrors list is located:
```
/etc/pacman.d/mirrorlist
```
On debian based systems its:
```
/etc/apt/sources.list
```

## Setting up reflector to work automatically
The following command will setup reflector to automatically update the mirrorslist once a week by default:

```
sudo systemctl enable reflector.timer
sudo systemctl start reflector.timer
```

## Everything is a file 
Unix design philosophy. Widely regarded as most defining principle in Unix.
The main idea is to provide a unified interface of accessing wide range of input/output resources like printers, monitors, directories, terminals, modems, keyboards, mouses, hard-drivers and even some inter-process communications and network communication. This common abstraction for all these resources the unix fathers called a 'file'. 
Since every file is exposed through the same file



### References

