## Arch Linux Installation Guide

### Using UTM for mac
- Emulation so very slow

### Install
1. Download ISO from the Arch Linux website.
2. Using x86_64 emulation:
    - Allocate 10GB of RAM.
3. Boot into the live environment.
4. Partition the disks (UEFI system):
    - View current disks: `fdisk -l`
    - Create partitions using `fdisk`:
      - `sda1`: EFI System Partition - 1GiB
      - `sda2`: Linux Swap - 6GiB
      - `sda3`: Linux x86-64 - rest of the disk (5GB extra space)
    - Save the changes.
5. Format the disks:
    - Root: `mkfs.ext4 /dev/sda3`
    - Swap: `mkswap /dev/sda2`
    - EFI System Partition: `mkfs.fat -F32 /dev/sda1`
6. Mount the file systems:
    - `mount /dev/sda3 /mnt`
    - `mkdir /mnt/boot`
    - `mount /dev/sda1 /mnt/boot`
    - `swapon /dev/sda2`
7. Install base packages using `pacstrap`:
    - `pacstrap /mnt base linux linux-firmware`
    - Additional packages: `intel-ucode e2fsprogs sof-firmware netctl nano man-db man-pages texinfo`
    - At this point in the future: Install a DHCP Client
8. Generate `fstab` file:
    - `genfstab -U /mnt >> /mnt/etc/fstab`
9. Change root into the new system:
    - `arch-chroot /mnt`
10. Set the time zone:
     - `ln -sf /usr/share/zoneinfo/Region/City /etc/localtime`
     - can't use `timedatectl`
     - `hwclock --systohc`
11. Set locale:
     - Edit `/etc/locale.gen` and uncomment `en_US.UTF-8 UTF-8`
     - `locale-gen`
     - `echo "LANG=en_US.UTF-8" > /etc/locale.conf`
12. Set hostname:
     - `echo "Holden-Arch" > /etc/hostname`
13. Set root password:
     - `passwd`

### Install Desktop Environment
1. Connect to WiFi:
    - Use `systemd-networkd` (not `netctl` if you don't have a DHCP Client).
2. Install Budgie desktop environment:
    - `pacman -S budgie-desktop`
3. Install Nautilus file manager:
    - `pacman -S nautilus`
4. Configure `~/.xinitrc`:
    - `XDG_CURRENT_DESKTOP=Budgie:GNOME`
5. Install LightDM display manager:
    - `pacman -S lightdm 
    - Enable LightDM: `systemctl enable lightdm`
    - Should Have enabled a Greeter but didn't - Used TTYL to install LightDM GTK Greeter (the default) 

6. Install Terminator terminal emulator:
    - `pacman -S terminator`

### Users
1. Add user:
    - `useradd -m -G wheel holden`
    - `passwd holden`
    - Set password: `gunner`
2. Do the same for Codi and Justin
    - password: "GraceHopper1906"

### Other
1. Install Zsh shell:
    - `pacman -S zsh`
2. Install SSH:
    - `pacman -S openssh`
3. Set color preferences for Terminator using GUI.


#### Aliases
- `alias c='clear'`
- `alias cd1='cd ../'`
- `alias cd2='cd ../../'`

### Problems
- **Pacman not working**:
  - Error: Failed to synchronize all databases (unexpected error)
- Started with a clean install and it fixed our issue... i think i must have installed a package incorrectly
- **DHCP Client**:
  - Orginally used Netctl but did not have a DHCP client installed so switched to `systemd-networkd`.
- Next time, I will choose a DHCP client
- **LightDM not booting**:
- It said that boot failed because I did not have a boot helper.
  - Solution: Use `Ctrl + Alt + F7` to boot into command line and install the helper.

  ### General Notes
  - `Ctrl +Alt +F7` goes to Typewriter mode which is not only faster when emulating but also can fix issues if you are having gui issues
  - Would not want to use this VM for normal use as emulation is just too slow to be practical

<!--
- Using UTM
- Go to ttyl option-control-fn- fkeys
## Install
1. Download ISO from Arch Website
2. Using a x86_64 Emulation 
	1. 10gb of ram
3. Boot into Live Environment
4. Partition the disks
	- I have a UEFI system so I made 3 partitions - Using fdisk
		- view current disks with fdisk -l
		- sda/1 to be boot - EFI System Partition - 1GiB
		- sda/2 to be Swap - Linux Swap - 6GiB
		- sda/3 to be Root - Linux x86-64 - rest of disk - 5Gb for extra space just in case
		- Save the changes 
		- 
1. Format the Disks
	- Root - ext4
	- Swap - mkswap
	- EFI System Partition - 
2. Mount the File Systems!
3. install package using pacstrap (not pacman)
	1. pacstrap -K /mnt base linux linux-firmware
	2. intel-ucode, e2fsprogs, sof-firmware, netctl, nano, man-db, ma-pages, texinfo
4. Create a fstab file
	1. genfstab -U /mnt >> /mnt/etc/fstab
5. chroot into arch
	1. arch-chroot /mnt
6. Set the time zone
7. Set Locale File
8. Set Hostname as Holden-Arch
9. Set Password - HoldenArch
10. Redid everything with a clean install to fix issues


## Install Desktop Environment
- First I needed to connect to wifi
	- Used Systemd-Networkd
	- Not netctl
- Decided to use Budgie for my desktop environment - pacman -S budgie
- Nautilus file manager
- ~/.xinitrc
- LightDM as my Display Manager
- Installed Terminator for a Terminal Emulator
- 

## Users
	'useradd -m -G wheelholden`
	`passwd holden`
PASSWORD: gunner


export XDG_CURRENT_DESKTOP=Budgie:GNOME
exec budgie-desktop
- 

## Other
`pacman -S zsh`
`pacman -S ssh`
Used the preferences on my GUI to set color preferences for terminator - my terminal
#### Alias
- `alias c='clear'
- `alias cd1=' cd ../'
- `alias cd2= 'cd ../../'`
- `

### Problems
- Pacman not working 
	- Failed to synchronize all databases (unexpected error)
	- Started from scratch and 
	- 
	- DHCP Client?
		- Didn't have on installed so pivoting to systemd networkd
- I didn't install a helper with LightDM so it wouldn't boot, but I figured out that function control option f7 would boot into command line and installed the helper
-->

