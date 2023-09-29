
# First Build Night 2023

!!! note ""
    #### [The Slideshow](https://docs.google.com/presentation/d/1W4XjEZBrX7zmOMw1fc-9jNLmA-6al6T6Ukz_EMm00iE/edit#slide=id.g284792d178a_3_17)
    #### [Onboarding Video](https://drive.google.com/file/d/1_4ZWfHGMSUpgvX0lv68FG9j0RoAQPBAW/view?usp=drive_link)

## Software

### VSCode and WPILib

We program Java using VSCode. Specifically WPI VScode downloadable [here](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html).
This cannot be downloaded on chromebooks, so a windows computer will be preferrable.

### Git and Github

Version control is important because it allows everyone to work together. We use Github to store our codebase. If you are not on the Github,
contact the programming leads.

We suggest using Gitkraken, but if you want to work on private repositories for free, use Github Desktop. [Download Git](https://git-scm.com/downloads), [Github Desktop](https://desktop.github.com/) and [GitKraken](https://www.gitkraken.com/download).

Guides for Usage made soon maybe.

### Advantage Kit and Advantage Scope

"Logging" is an important part of debugging. If the robot malfunctions, we can check the logs for what went wrong. Advantage Kit works in a very special way. It allows us to push specific data through NetworkTables and Media by the radio or USB stick. We can view these files while the robot is running through Network Tables, or after the robot is turned off using Advantage Scope.

Install Advantage Scope [here](https://github.com/Mechanical-Advantage/AdvantageScope/releases).

Guides and usages made soon, again maybe.

## Arm Example Code

```java title="Arm.java"
public class Arm {

    private TalonComponent tiltMotor;
    private SparkMaxComponent extentionMotor;
    private double targetTiltAngle;
    private double targetExtention;

    /**
     * Constructor for the arm.
     * Initializes motors
     * @author Saaleh Poovathumkadavil
     */
    public Arm() {
        this.tiltMotor = new TalonComponent(1, "TalonSRX");
        this.extentionMotor = new SparkMaxComponent(2, MotorType.kBrushless);
    }

    public void setTilt(double tiltAngle) {
        targetTiltAngle = tiltAngle;
        tiltMotor.setAngle(tiltAngle);
    }

    public double getTilt() {
        return targetTiltAngle;
    }

    public void setExtention(double extention) {
        targetExtension = extension;
        extentionMotor.setAngle(extention);
    }

    public double getExtention() {
        return targetExtention;
    }

    @Override
    public void initSendable(SendableBuilder builder) {
        builder.addDoubleProperty("Target Tilt Angle", () => targetTiltAngle, null);
        builder.addDoubleProperty("Target Extionsion", () => targetExtention, null);
    }

}
```
