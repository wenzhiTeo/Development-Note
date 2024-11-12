# To shrinking the virtual drive to its actual size

## CMD
wsl --list --verbose

wsl --shutdown

diskpart


## Diskpart
**Clean docker**
select vdisk file="C:\Users\TeoWenZhi\AppData\Local\Docker\wsl\data\ext4.vhdx"

compact vdisk

**Clean ubuntu**
select vdisk file="C:\Users\TeoWenZhi\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu22.04LTS_79rhkp1fndgsc\LocalState\ext4.vhdx"

compact vdisk
