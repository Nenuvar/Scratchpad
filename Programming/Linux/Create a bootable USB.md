Download the Linux ISO file

Verify the ISO (version-dependent)

Flash the ISO onto the USB using dd in the Crostini terminal:
`sudo dd if=path_to_linux_lite.iso of=/dev/sda bs=4M status=progress && sync`

Replace path_to_linux_lite with the name of the ISO you downloaded

`/dev/sda` is the path to the USB. Check with:
`lsblk`

If the USB isn't listed, see “Make USB visible in Linux Crostini on ChromeOS”

Unmount the USB from the terminal:
`sudo unmount /dev/sda`

Adjust `/dev/sda` if your USB has a different identifier

Unmount the USB by toggling off the Linux apps permission in settings

The USB should now be visible in your Files app
