# To shrinking the virtual drive to its actual size

## CMD
wsl --list --verbose
wsl --shutdown
diskpart


## Diskpart
select vdisk file="C:\Users\TeoWenZhi\AppData\Local\Docker\wsl\data\ext4.vhdx"
compact vdisk
