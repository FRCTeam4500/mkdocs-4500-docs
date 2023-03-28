# Motor Controllers

## Spark Max Controllers

Spark Max Controllers are typically used to control 'neos'. This is a very common form of motor, and is widely used across the robot.

### How to Program a SparkMax Controller?

Programming a SparkMax controller in Java can be done using the CTRE Phoenix Framework. This framework provides an API for controlling and communicating with various CTRE products, including the SparkMax motor controllers. Here is a step by step overview of how to program a SparkMax motor controller in Java:

!!! note
    This includes SparkMaxComponent.java

1.  Install the CTRE Phoenix Framework: You can download the latest version of the CTRE Phoenix Framework from the CTRE website.

2.  Import the necessary libraries: Before you can start programming the SparkMax, you need to import the necessary libraries into your Java project.
```java
import com.ctre.phoenix.motorcontrol.ControlMode; 
import com.ctre.phoenix.motorcontrol.can.TalonSRX; 
import com.ctre.phoenix.motorcontrol.can.VictorSPX;
```

3.  Create an instance of the SparkMax class: To communicate with a SparkMax motor controller, you need to create an instance of the `TalonSRX` or `VictorSPX` class, depending on the type of SparkMax motor controller you are using.
```java
TalonSRX motor = new TalonSRX(1);
```

4.  Configure the motor controller: Before you can start using the SparkMax motor controller, you need to configure it. You can do this by calling the `configure()` method and passing in the desired settings.
```java
motor.configFactoryDefault();
```



5.  Control the motor: Once the SparkMax motor controller has been configured, you can start controlling it. You can control the motor by setting its output using the `set()` method and passing in the desired control mode and output value.
```java
motor.set(ControlMode.PercentOutput, 0.5);
```

6.  Read feedback from the motor: To get feedback from the SparkMax motor controller, you can read its position, velocity, or current. You can do this by calling the appropriate getter method, such as `getSelectedSensorPosition()`, `getSelectedSensorVelocity()`, or `getOutputCurrent()`.
```java
int position = motor.getSelectedSensorPosition();
```

7.  Close the motor: Once you are done using the SparkMax motor controller, you should close it by calling the `close()` method.
```java
motor.close();
```

### Run SparkMax via Position
!!! warning inline end
    Make sure you set kP, kI, and kD valued before setting the motor to a position. They default to no values, and this means the motor will not run.

`ControlMode.Position` is a control mode in the SparkMax motor controller that allows the motor to be commanded to a specific position, rather than a specific speed or voltage. In other words, it allows the motor to move to a **specific angular position** and hold that position, instead of continuously rotating at a set speed. The motor controller will use its closed-loop control algorithms to regulate the motor's movement and maintain the desired position. This mode is often used for applications where precise positioning of a motor is required, such as in robotic arms, grippers, and other similar mechanisms.

### How to see position value for a SparkMax Controller?

The value of the position you would like to tilt your motor to can be determined through a combination of trial and error and mathematical calculation. To start, you may use trial and error to get an estimate of the desired position. You can then use the following formula to refine the value:

position = (desired angle / 360) * counts per revolution

where "desired angle" is the angle you want the motor to reach, and "counts per revolution" is the number of counts (encoder ticks - 42 for neo BM V1.1) the motor generates per revolution. The counts per revolution value can be found in the motor's specifications or from experimentation.

You can put this value on Shuffleboard wither manually using
```java
Shuffleboard.getTab("Tab Name").add(() -> subsystem.motor.getEncoder.getPosition())
```

Or, you can override the initSendable method inside of the subsystem file itself.

``` java linenums="1" hl_lines="2"
public void initSendable(SendableBuilder builder) {
	builder.addDoubleProperty("Current Motor Position", () -> motor.getEncoder().getPosition(), null)
}
```

A [lambda](../java.md#lambda-expressions) expression `() ->` is used in place of the value itself, because the value needs to update. The type of the argument needs to be that of a [supplier](../java.md#suppliers-consumers-and-subscribers).

Additionally, there are software tools such as the WPILib's SmartDashboard or CTRE's **Phoenix Tuner** that can be used to visualize the motor's position and assist with determining the desired position. These tools can also be useful for fine-tuning the motor's position control during testing and competition.

### Sample Code Using Positions

```java
public class ArmControl { 
	private CANSparkMax armMotor; 
	
	// Encoder values for each position 
	private final int GROUND = 0; 
	private final int BOTTOM = 1000; 
	private final int MIDDLE = 2000; 
	private final int TOP = 3000; 
	private final int RETRACTED = 4000; 
	
	public ArmControl() { 
		// Initialize the SparkMax motor controller for the arm motor 
		armMotor = new CANSparkMax(1, MotorType.kBrushless); 
		
		// Configure the SparkMax controller for position control 
		armMotor.setIdleMode(IdleMode.kBrake); // Applies brakes
		armMotor.setInverted(false); 
		armMotor.setOpenLoopRampRate(0.0); 
		armMotor.setClosedLoopRampRate(0.0); 
		armMotor.setSensorPhase(false); 
		armMotor.setSelectedSensorPosition(0); 
		
		// Set the control mode of the SparkMax controller to position 
		armMotor.set(ControlMode.Position, GROUND); 
	} 
}
```
You can modify the `ArmControl` class to move the arm to the different positions by changing the target position in the `armMotor.set(ControlMode.Position, TARGET_POSITION)` line. For example, to move the arm to the "middle" position, you would set `TARGET_POSITION` to `MIDDLE`.

The `setIdleMode(IdleMode.kBrake)` method sets the idle mode of the arm motor. The idle mode determines how the motor behaves when it's not receiving a signal from the controller. There are two options for idle mode: coast and brake. 
- When in brake mode, the motor will apply brakes to hold its position when it's not being commanded to move. This can be useful when you want the motor to stay in a certain position even when the power to the motor controller is turned off.
- When in coast mode, the motor will not apply brakes, but will instead coast to a stop when it's not being commanded to move. This can be useful when you want the motor to continue rotating after it loses power, or when you want to minimize the amount of energy consumed by the motor.

The `setOpenLoopRampRate` method sets the maximum rate at which the output of the motor controller can change. This can be useful in certain control scenarios to prevent abrupt changes in the motor output. By setting this ramp rate, you control how quickly the motor controller can transition from one power level to another. This helps reduce the chances of damaging the motor and other components, as well as smoothing out any sudden jerks in motion. For example, if you set the ramp rate to 0.5 seconds, the motor controller will take 0.5 seconds to change its output power from 0 to 100%. The rate is specified in seconds to reach full output.

`armMotor.setClosedLoopRampRate` sets the rate at which the output of the motor controller will change when in closed-loop control modes (e.g. position, velocity, and current control modes), while `armMotor.setOpenLoopRampRate` sets the rate at which the output of the motor controller will change when in open-loop control motor.
- In closed-loop control modes, the motor controller receives feedback from the motor's position, velocity, or current and adjusts its output to achieve the desired value. In open-loop control mode, the motor controller simply sets the output based on the input value, without any feedback or correction.
- The ramp rate is used to limit the rate of change of the motor output, in order to prevent excessive currents and protect the motor, gearbox, and other components. A slow ramp rate allows the motor output to change smoothly over time, reducing the risk of damage, while a fast ramp rate allows the motor to quickly reach its desired speed. The ramp rate values are typically specified in units of voltage per second.

The `setSensorPhase` method is used to specify the sensor phase of the motor controller. In other words, it sets whether the sensor position increases or decreases as the motor moves in a forward direction. If the `setSensorPhase` is set to true, the sensor position will increase as the motor moves in the forward direction. If it is set to false, the sensor position will decrease as the motor moves in the forward direction.
- It is important to set the sensor phase correctly because incorrect sensor phase can cause the motor to behave unexpectedly, such as moving in the opposite direction of what is intended, or moving erratically. The correct value for the sensor phase can be determined experimentally by observing the motor behavior and making adjustments until it behaves as desired.
