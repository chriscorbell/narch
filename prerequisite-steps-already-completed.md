- Write archlinux-2026.09.01-x86_64.iso to a USB stick (GPT partition scheme for UEFI) using Rufus on a Windows 11 machine

- Boot from the USB, connect to network and then run `archinstall`
    - Select mirror region
    - "Disk Configuration" > "Partitioning" > "Use a best-effort default partition layout"
    - Choose disk, choose `ext4`, no separate partition for `/home`, no LVM or encryption
    - Set hostname and authentication
    - Profile > "Minimal"
    - Applications > enable Bluetooth, enable PipeWire for audio
    - Network > "Use Network Manager (default backend)"
    - Set timezone
    - Install, then reboot into installed system

- I'm currently using a Latitude 9450 which requires some GPU/display fixes:
    - Find active systemd-boot entry: `bootctl list`
    - Edit the entry file shown under source, for example: `sudo nano /boot/loader/entries/arch.conf`
    - Find the `options` line and add this argument: `i915.enable_psr=1`
    - Save the file and reboot: `sudo reboot`

- Installed nano, git, less