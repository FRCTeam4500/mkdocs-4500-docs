# PID

$$u(t)=K_{\text{p}}e(t)+K_{\text{i}}\int _{0}^{t}e(\tau )\,\mathrm {d} \tau +K_{\text{d}}{\frac {\mathrm {d} e(t)}{\mathrm {d} t}}$$

!!! note
    You don't need to know the math because we are going to be using a predefined method instead of  theoretical math.

The _kP_, _kI_, and _kD_ values can be adjusted to optimize the performance of the PID controller for the specific robot and conditions it will be operating in. The optimal values for these gains will depend on the specific characteristics of your robot, including the weight distribution, motor performance, drivetrain responsiveness, and other factors.

_kP_ is how much the PID oscillates.

_kI_ is the speed at which you reach the ideal value but that can lead to overshooting if it's too high.

_kD_ dampens oscillation but can have problem with response time if too high. Dampening of oscillation is related to response time because if the dampening is too large, the robot won't be able to respond to overshooting as quickly.

## Tuning PID Controllers
It can be done through a process of trial and error, where the gains are adjusted incrementally and the resulting behavior of the robot is observed. Here are some general guidelines for tuning the PID controller:

1.  Start with _kP_ at 0.1, _kI_ at 0.01, and _kD_ at 0.01.
    
2.  Increase the value of _kP_ until the robot starts to **oscillate**. Then set the value to half.
    
3.  Adjust the value of _kI_ until the robot hits the target angle at as fast a time as possible (which happens with higher _kI_ value), but a value less than a value where there's creeping overshooting.
    
4.  Adjust the value of _kD_ to **dampen the oscillations** of the robot. A high value of _kD_ will reduce the **amplitude** of the oscillations, but may also slow down the **response time** of the robot.
    
5.  Repeat the process of adjusting the gains until the robot maintains balance on the charging station with **minimal oscillation**.

!!! warning
    Using `I` and `D` values can be quite tricky. It is totally possible to get by with just the `P` term.