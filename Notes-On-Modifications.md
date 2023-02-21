# Notes on possible modifications to the mounted W10M FFU

This document is going to be a work in progress as I figure things out (all info here is subject to change, advised not to use this info yet), but here you can find info on what can be done, and what cannot be done to a mounted FFU

Links will be added to some items after tests have been done, items with (??) at the end are "To Be Confirmed"

## How to access the mounted FFU
- Take note of where `wpimage` mounts the FFU:
```
Initializing full flash update image C:\Staging\RM1104_15254_unsigned.ffu.
Mounting the full flash update image.
ETW Log Path: C:\Users\EMPYRE~1\AppData\Local\Temp\storage_session_d24.etl
OS Version: Microsoft Windows NT 10.0.19045.0
OpenDiskInternal: Creating empty virtual disk.
OpenDiskInternal: Mounted virtual disk at phys \\?\PhysicalDrive1
Storage Service: Created a new image in 0.1 seconds.
        Main Mount Path: C:\Users\Empyreal96\AppData\Local\Temp\bigodjvd.0um.mnt\     <-- This is what to look out for -->
        Physical Disk Name: \\.\PhysicalDrive1
```
- Simply open that directory in Explorer to view the mounted images files


## What can be done
Not much to put here yet

- Install the Unsigned Developer Menu to the FFU if you plan to run `wpinternals.exe -EnableTestSigning` after flashing (Add a mount point to MainOS in Disk Management, e.g K:\)
- Create UEFIChargingLogToDisplay.txt in `{MainOS}:\EFIESP\Windows\System32\Boot` to show UEFI Charging logs on-screen during boot (??)
- Push [Tshell Update](https://www.youtube.com/watch?v=MuHGy4Yei7o) to the device with UpdateApp and create [startup.bsc]() in `{MainOS}:\Windows\System32` (??)



## What can't be done
- Modifying the registry -- this is because the manifests required to edit to add new/modified registry values are compressed, while there are ways to decompress the manifests, I have no idea how to compress them back up! And Windows won't boot if we have uncompressed manifests.. Only info I know is that they get compressed with MS's Delta API (msdelta.dll) (Todo: add links with info/decompression tools)
- 
