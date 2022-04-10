# Help
`fastboot help`

# Devices
Show devices attached:

`fastboot device`

Show devices/transport_id:

`fastboot devices -l`

# Reboot
Reboot device:

`fastboot reboot`

Go to bootloader mode:

`fastboot reboot bootloader`

From android 10, android support dynamic partitions (flashing in fastbootd).
To go to fastbootd:

`fastboot reboot fastboot`

# Get bootloader variables

`fastboot getvar [pattern]`

Examples:

- Get all bootloader variables:

`fastboot getvar all`

- Get bootloader version:

`fastboot getvar version-bootloader`

# Flashing

Flash a partition:

`fastboot flash [partition_name] [partition_name.xxx]`

Flash all:

`fastboot flashall`

Update from zip file (without wipes `/data` partition);

`fastboot update xxx.zip`

Update from zip file (with wipes `/data` partition):

`fastboot update -w xxx.zip`

Note: Before flashing use flashall or update feature, fastboot tool will check the parameters in android.txt first,
If have some mistakes, the flashing process will be existed.

# Locking/Unlocking

Lock/unlock partitions:

`fastboot flashing lock|unlock`

Lock/unlock bootloader partitions:

`fastboot flashing lock_critical|unlock_critical`

Check whether unlocking is allowed (1) or not (0):

`fastboot flashing get_unlock_ability`

# Options
`-w`                         Wipe userdata.

`-s SERIAL`                  Specify a USB device.

`-s tcp|udp:HOST[:PORT]`     Specify a network device.

`-S SIZE[K|M|G]`             Break into sparse files no larger than SIZE.

`--force`                    Force a flash operation that may be unsafe.

`--slot SLOT`                Use SLOT; 'all' for both slots, 'other' for
                             non-current slot (default: current active slot).

`--set-active[=SLOT]`        Sets the active slot before rebooting.

`--skip-secondary`           Don't flash secondary slots in flashall/update.

`--skip-reboot`              Don't reboot device after flashing.

`--disable-verity`           Sets disable-verity when flashing vbmeta.

`--disable-verification`     Sets disable-verification when flashing vbmeta.

`--fs-options=OPTION[,OPTION]`
                             Enable filesystem features. OPTION supports casefold, projid, compress

`--wipe-and-use-fbe`         Enable file-based encryption, wiping userdata.

`--unbuffered`               Don't buffer input or output.

`--verbose, -v`              Verbose output.

`--version`                  Display version.

`--help, -h`                 Show this message.

