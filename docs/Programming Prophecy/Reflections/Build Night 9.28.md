
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
public class Arm extends SubsystemBase { // Creates an Arm Class (1)!

    private SparkMaxComponent tiltMotor; // Declares a tiltMotor of the TalonComponent class (2)!
    private TalonComponent extentionMotor; // Declares an extentionMotor of the SparkMaxComponent Class (3)!
    private double targetTiltAngle;
    private double targetExtention;

    /**
     * Constructor for the arm.
     * Initializes motors
     * @author Saaleh Poovathumkadavil // (4)
     */
    public Arm() { // (5)
        this.extentionMotor = new TalonComponent(1, TalonMotor.TalonSRX); // (6)!
        this.tiltMotor = new SparkMaxComponent(2, MotorType.kBrushless); // (7)1
    }

    public void setTilt(double tiltAngle) { // (8)!
        targetTiltAngle = tiltAngle;
        tiltMotor.setAngle(tiltAngle);
    }

    public double getTilt() { // (9)!
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
    public void initSendable(SendableBuilder builder) { // (10)
        builder.addDoubleProperty("Target Tilt Angle", () => targetTiltAngle, null); // (11)!
        builder.addDoubleProperty("Target Extionsion", () => targetExtention, null);
    }

}
```

1.  In this case, we are creating a Arm Subsystem. 
    The `SubsystemBase` is a class provided by WPILib that we can extend.
    By doing so, we can ensure that the `Arm` Class has every attribute and method
    of the `SubsystemBase` class.

2.  The 2023 Robot, Dwayne The Bot Johnson, uses a NEO motor for Tilt.
    This motor is controlled by a Spark Max motor controller.
    Our implementation of this is in the file `SparkMaxComponent`
    which extends `CANSparkMax`

3.  The 2023 Robot, Dwayne The Bot Johnson, uses a 775pro motor for Tilt.
    This motor is controlled by a Talon SRX controller.
    Our implementation of this is in the file `TalonComponent`
    which extends `BaseTalon`. This can translate to Talon FX Controllers as well,
    needs specification in TalonMotor enum.