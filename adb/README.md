# Help
`adb help`

# Reboot
Reboot device:

`adb reboot`

Go to bootloader (fastboot):

`adb reboot bootloader`

From android 10, android support dynamic partitions (flashing in fastbootd).
To go to fastbootd:

`adb reboot fastboot`

Go to recovery mode:

`adb reboot recovery`

Go to Emergency Download Mode (EDL) of qualcomm device:

`adb reboot edl`

# Devices
Show devices attached:

`adb devices`

Show devices/product/model/transport_id:

`adb devices -l`

# Logcat
Show logs:

`adb logcat [-b <buffer>]`

With buffer is:

`main`: View the main log buffer (default) does not contain system and crash log messages.

`kernel`: View the kernel log buffer.

`system`: View the system log buffer (default).

`radio`: View the buffer that contains radio/telephony related messages.

`events`: View the interpreted binary system event buffer messages.

`crash`: View the crash log buffer (default).

`all`: View all buffers.

`default`: Reports main, system, and crash buffers.

Refers to: https://developer.android.com/studio/command-line/logcat#alternativeBuffers

Clear logcat:

`adb logcat -c`

# Get bugreport

`adb bugreport`

# App installation

`adb install [options] path/to/app.apk`

Options:

`-r`: Reinstall an existing app, keeping its data.

`-t`: Allow test APKs to be installed. Gradle generates a test APK when you have only run or debugged your app or have used the Android Studio Build >
Build APK command. If the APK is built using a developer preview SDK (if the targetSdkVersion is a letter instead of a number), you must include the -t option with the install command if you are installing a test APK.

`-i` installer_package_name: Specify the installer package name.

`--install-location` location: Sets the install location using one of the following values:
  0: Use the default install location.
  1: Install on internal device storage.
  2: Install on external media.

`-f`: Install package on the internal system memory.

`-d`: Allow version code downgrade.

`-g`: Grant all permissions listed in the app manifest.

`--fastdeploy`: Quickly update an installed package by only updating the parts of the APK that changed.

`--incremental`: Installs enough of the APK to launch the app while streaming the remaining data in the background. To use this feature, you must sign the APK, create an APK Signature Scheme v4 file, and place this file in the same directory as the APK. This feature is only supported on certain devices. This option forces adb to use the feature or fail if it is not supported (with verbose information on why it failed). Append the --wait option to wait until the APK is fully installed before granting access to the APK.

`--no-incremental` prevents adb from using this feature.

# App uninstallation

`adb shell pm uninstall package_app_name`

# Activity manager (am)

Broadcast intent:

`adb shell am broadcast [options] intent`

Options are:

`--user` user_id | all | current: Specify user whose processes to kill; all users if not specified.

Start an activity of an application:

`adb shell am start -n [package_name]/[activity_name]`

Force stop a package:

`adb shell am force-stop [package_name]`

Kill package:

`adb shell am kill [options] [package_name]`

Options are:

`--user` user_id | all | current: Specify user whose processes to kill; all users if not specified.

Enter device to test mode (to bypass setup wizard):

`adb shell am broadcast -a com.google.android.clockwork.action.TEST_MODE`

# Package manager (pm)

List all packages:

`adb shell pm list packages [options]`

Options:

`-f`: See their associated file.

`-d`: Filter to only show disabled packages.

`-e`: Filter to only show enabled packages.

`-s`: Filter to only show system packages.

`-3`: Filter to only show third party packages.

`-i`: See the installer for the packages.

`-u`: Also include uninstalled packages.

`--user` user_id: The user space to query.

Clear all data of a package:

`adb shell pm clear [package_name]`

List all users of the system:

`adb shell pm list users`

List all permissions:

`adb shell pm list permissions`

`adb shell pm list permission-groups`

# Dump system
List of system services that you can use with dumpsys:

`adb shell dumpsys -l`

`adb shell dumpsys -l | grep -i [pattern]`

Dump a service:

`adb shell dumpsys [service] [args]`

Examples:

- Dump input service:

`adb shell dumpsys input`

- Dump battery service and set ac mode:

`adb shell dumpsys battery set ac 0`

- Dump display service and get screen state:

`adb shell dumpsys display | grep "mScreenState"`

- Force system into idle mode:

`adb shell dumpsys deviceidle force-idle`

- Exit idle mode:

`adb shell dumpsys deviceidle unforce`

# Input events
Get all events:

`adb shell getevent -l`

Simulate key event:

`adb shell input keyevent [KEY_CODE]`

KEY_CODE: https://developer.android.com/reference/android/view/KeyEvent#constants_1

Simulate touch event:

- Tap X,Y position:

`adb shell input tap x y`

- Swipe X1,Y1 --> X2,Y2 with duration (ms):

`adb shell input swipe [x1] [y1] [x2] [y2] [duration]`

- Long press X,Y

`adb shell input swipe [x] [y] [x] [y] [duration]`

Simulate text event:

`adb shell input text 'text'`

