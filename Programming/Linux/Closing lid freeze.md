For the Suspend fix (prevent freezing after lid close), here are the detailed commands:

1. Edit the logind.conf file: Run this command to open the file in a text editor:
`sudo nano /etc/systemd/logind.conf`

2. Modify the file:

Find the line that contains `#HandleLidSwitch=suspend`

Uncomment the line (remove the # at the beginning) and change suspend to ignore so it looks like this:

`HandleLidSwitch=ignore`

3. Save and exit:
Press `Ctrl + O` to save the changes.
Press `Enter` to confirm the file name.
Press `Ctrl + X` to exit the editor.

4. Restart systemd-logind: To apply the changes without rebooting, restart the systemd-logind service:
`sudo systemctl restart systemd-logind`

Alternatively, you can reboot the system:
`sudo reboot`

This will prevent the system from freezing when the lid is closed by instructing it to ignore the lid switch.

