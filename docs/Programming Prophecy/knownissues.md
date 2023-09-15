# Known Issues for 2023

This article details known issues (and workarounds) for FRC Control
System Software.

## Open Issues

### roboRIO 2.0 Ethernet Settings

**Issue:** On the roboRIO 2.0, the Ethernet port is configured to DHCP
only. This will work in normal networking setups where the radio acts as
a DHCP server, but will not communicate when tethered directly to the
Driver Station via Ethernet.

**Workaround:** Use the
`roborio web dashboard` to change the Ethernet Adapter eth0 `Configure IPv4 Address` to `DHCP or Link Local`.

### Driver Station Reporting No Code

**Issue:** There is a rare occurrence in the roboRIO 2.0 that causes the roboRIO to not properly start the robot program. This causes the Driver Station to report a successful connection but no code, even though code is deployed on the roboRIO.

**Workaround:** We are currently investigating the root cause, but FIRST volunteers have been made aware and the recommendation is to reboot the roboRIO when this occurs.

!!! note
    Pressing the physical `User` button on the roboRIO for 5 seconds can also cause the robot code to not start, but a reboot will not start the robot code. If the robot code does not start after rebooting, press the `User` button. Ensure that nothing on the robot is in contact with the `User` button.


### Radio Second Port Sometimes Fails to Communicate

**Issue:** There is a rare occurrence in the OM5P Radios that causes the second Ethernet port (the one farthest from the power plug) to not communicate.

**Workaround:** Generally, power cycling the radio will restablish communication with the second port. Alternately, utilize a network switch such as the tp-link switch available from [FIRST Choice](https://firstchoicebyandymark.com/fc-cn-9024) or the [brainboxes SW-005](https://www.brainboxes.com/product/industrial-ethernet-switches/fast-ethernet/sw-005) and plug all ethernet devices into the network switch and then plug the switch into the radio's first Ethernet port. This also allows easier tethering while at competition.

### Onboard I2C Causing System Lockups

**Issue:** Use of the onboard I2C port, in any language, can result in system lockups. The frequency of these lockups appears to be dependent on the specific hardware (i.e. different roboRIOs will behave differently) as well as how the bus is being used.

**Workaround:** The only surefire mitigation is to use the MXP I2C port or another device to read the I2C data. Accessing the device less frequently and/or using a different roboRIO may significantly reduce the likelihood/frequency of lockups, it will be up to each team to assess their tolerance of the risk of lockup. This lockup can not be definitively identified on the field and a field fault will not be called for a match where this behavior is believed to occur. This lockup is a CPU/kernel hang, the roboRIO will completely stop responding and will not be accessible via the DS, webpage or SSH. If you can access your roboRIO via any of these methods, you are experiencing a different issue.

Several alternatives exist for accessing the REV color sensor without using the roboRIO I2C port. A similar approach could be used for other I2C sensors.

-   Use a [Raspberry Pi Pico](https://github.com/ThadHouse/picocolorsensor/). Supports up to 2 REV color sensors, sends data to the roboRIO via serial. The Pi Pico is low cost (less than $10) and readily available.
-   Use a [Raspberry Pi](https://github.com/PeterJohnson/rpi-colorsensor/). Supports 1-4 color sensors, Primarily useful for teams already using a Raspberry Pi as a coprocessor.

### Updating Properties on roboRIO 2.0 may be slow or hang

**Issue:** Updating the properties on a roboRIO 2.0 without reformatting using the Imaging Tool (such as setting the team number) may be slow or hang.

**Workaround:** After a few minutes of the tool waiting the roboRIO should be able to be rebooted and the new properties should be set.

### Simulation crashes on Mac after updating WPILib

**Issue:** On macOS, after updating the project to use a newer version of WPILib, running simulation immediately crashes without the GUI appearing.

**Workaround:** In VS Code, run WPILib \| Run a command in Gradle, `clean`. Alternatively, run `./gradlew clean` in the terminal or delete the build directory.

### Invalid build due to missing GradleRIO

**Issue:** Rarely, a user's Gradle cache will get broken and they will get shown errors similar to the following:

``` console
Could not apply requested plugin [id: ‘edu.wpi.first.GradleRIO’, version: ‘2020.3.2’] as it does not provide a plugin with id ‘edu.wpi.first.GradleRIO’
```

**Workaround:**

Delete your Gradle cache located under `~$USER_HOME/.gradle`. Windows machines may need to enable the ability to [view hidden files](https://support.microsoft.com/en-us/windows/ view-hidden-files-and-folders-in-windows-10-97fbc472-c603-9d90-91d0-1166d1d9f4b5). This issue has only shown up on Windows so far. Please [report](https://github.com/wpilibsuite/frc-docs/issues/new) this issue if you get it on an alternative OS.

### Chinese characters in Driver Station Log

**Issue:** Rarely, the driver station log will show Chinese characters instead of the English text. This appears to only happen when Windows is set to a language other then English.

**Workaround:** There are two known workarounds:

1.  Copy and paste the Chinese characters into notepad, and the English text will be shown.
2.  Temporarily change the Windows language to English.

### C++ Intellisense - Files Open on Launch Don't Work Properly

**Issue:** In C++, files open when VS Code launches will have issues with Intellisense showing suggestions from all options from a compilation unit and not just the appropriate ones or not finding header files. This is a bug in VS Code.

**Workaround:**

1.  Close all files in VS Code, but leave VS Code open
2.  Delete c_cpp_properties.json file in the .vscode folder, if it exists
3.  Run the "Refresh C++ Intellisense" command in VS Code.
4.  In the bottom right you should see something that looks like a platform (linuxathena or windowsx86-64 etc). If it’s not linuxathena click it and set it to linuxathena (release)
5.  Wait \~1 min
6.  Open the main cpp file (not a header file). Intellisense should now be working

### Issues with WPILib Dashboards and Simulation on Windows N Editions

**Issue:** WPILib code using CSCore (dashboards and simulated robot code) will have issues on Education N editions of Windows.

-   Shuffleboard will run, but not load cameras
-   Smartdashbard will crash on start-up
-   Robot Simulation will crash on start-up

**Solution:** Install the [Media Feature Pack](https://www.microsoft.com/en-us/software-download/mediafeaturepack)

## Fixed in Game Tools 2023.1.0

### Driver Station does not detect joysticks at startup

**Issue:** The Driver Station application does not detect already connected joysticks when it starts up. Connecting joysticks after it is already running works.

**Workaround:** Connect joysticks after starting the DS, or use the joystick rescan button or the F1 shortcut to rescan for joysticks.

## Fixed in WPILib 2023.2.1

### SysId - Robot program crash on startup when using CAN Spark Maxes

**Issue:** SysId 2023.1.1's deployed robot program crashes on startup if it was configured to use CAN Spark Maxes.

**Solution:** Install WPILib 2023.2.1 or newer.

### Manually flushing a client NetworkTableInstance does not work

**Issue:** Calling `flush()` on a `NetworkTableInstance` does not cause the data to be flushed to remote subscribers immediately. This issue will be fixed in an upcoming WPILib release.

**Workaround:** Set the `periodic` option on the NetworkTable publishers that need a faster update rate:


```java
// Get a DoubleEntry for myTopic and update it with a 10ms period.
DoubleEntry myEntry = table.getDoubleTopic("myTopic").getEntry(0,
PubSubOption.periodic(0.01));
```

```cpp
// Get a DoubleEntry for myTopic and update it with a 10ms period.
nt::DoubleEntry entry = table.GetDoubleTopic("myTopic").GetEntry(0, {
.periodic = 0.01 });
```
