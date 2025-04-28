# Tech notes

- Make your USB visible in Linux Crostini on ChromeOS
    - Plug in the usb
    - share it with linux
    - Settings - about - Linux development environment - Manage usb devices - Give linux apps permission to access USB devices
        - the name of the usb should be listed. toggle this
        - Your usb is now visible in linux crostini
    - In linux run this command
        
        ```jsx
        lsblk
        ```
        
        This should list your usb as sda (or sdb or something other if you have several)
        
- Reset a read-only USB
    - Run this command
        
        ```jsx
        sudo mkfs.vfat /dev/sda
        ```
        
        - If this throws you an error, run
        
        ```jsx
        sudo mkfs.vfat -I /dev/sda
        ```
        
    - Unmount the usb from the terminal
        
        ```jsx
        sudo umount /dev/sda
        ```
        
    - Unmount the usb by toggling off the linux apps permission
    - The usb should now be visible, empty and readable in your files app
- Create a bootable USB
    - Download the Linux iso file
        - Verify the iso (dependent on the version)
    - Flash the iso onto the USB using dd in the crostini terminal.
        - In the linux terminal, write these commands to flash the iso image to the USB
        
        ```jsx
        sudo dd if=path_to_linux_lite.iso of=/dev/sda bs=4M status=progress && sync
        ```
        
        - path_to_linux_lite is replaced with the name of the iso you downloaded.
        - /dev/sda/ is the path to the USB. Use this command to check that Crostini can see it.
        
        ```jsx
        lsblk
        ```
        
        - If not listed, see “Make USB visible in Linux Crostini On ChromeOS”
    - Unmount the USB from the terminal:
        
        ```jsx
        sudo unmount/dev/sda
        ```
        
        - Remember to edit the /dev/sda if your USB is called something different
    - Unmount the USB by toggling off the linux apps permission in settings
    - Your USB should now be visible in your files app
- Install UEFI Firmware
    
    Follow MrChromebox’ instructions (only need to do once, so should be good)
    
- Boot from USB
    
    *Only plug in the USB when prompted!*
    
    - Power off your device
    - Power on. On the “Damaged OS”-menu, press ‘CTRL’ + ‘L’ to enter Legacy menu
    - At the “enter a numeric value for an alternative bootloader”, press any number key and wait approximately 30s - 1m
    - At the black screen with a white hare, quickly press ‘ESC’ to enter the boot screen
    - At the boot main menu:
        - **Insert your bootable USB**
    - From the “Boot menu” see that your USB is listed
        - The USB is NOT:
            - UEFI (terminal)
            - eMMC (Internal storage)
        - If it is not listed, try to unplug it for 5s at the main boot menu. Or choose another usb port
        - OR if that does not work, clear the USB and flash it again
    - Choose your USB and boot method.
    - Linux should boot