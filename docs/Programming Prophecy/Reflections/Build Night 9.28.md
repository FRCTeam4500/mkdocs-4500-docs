
# First Build Night 2023

<figure>
    <iframe src="https://docs.google.com/presentation/d/e/2PACX-1vRjP7974efchpUNOJoDRJTw309xEDDsAvcGuwFUhEPu6iHvx8ESbLhz36jsT6JKPyfTjPU16xzefxB5/embed?start=false&loop=false&delayms=3000" frameborder="0" width="640" height="396" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
</figure>

<figure>
    <style>.hytPlayerWrap{display:inline-block;position:relative}.hytPlayerWrap.ended::after{content:"";position:absolute;top:0;left:0;bottom:0;right:0;cursor:pointer;background-color:black;background-repeat:no-repeat;background-position:center;background-size:64px 64px;background-image:url(data:image/svg+xml;utf8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjgiIGhlaWdodD0iMTI4IiB2aWV3Qm94PSIwIDAgNTEwIDUxMCI+PHBhdGggZD0iTTI1NSAxMDJWMEwxMjcuNSAxMjcuNSAyNTUgMjU1VjE1M2M4NC4xNSAwIDE1MyA2OC44NSAxNTMgMTUzcy02OC44NSAxNTMtMTUzIDE1My0xNTMtNjguODUtMTUzLTE1M0g1MWMwIDExMi4yIDkxLjggMjA0IDIwNCAyMDRzMjA0LTkxLjggMjA0LTIwNC05MS44LTIwNC0yMDQtMjA0eiIgZmlsbD0iI0ZGRiIvPjwvc3ZnPg==)}.hytPlayerWrap.paused::after{content:"";position:absolute;top:70px;left:0;bottom:50px;right:0;cursor:pointer;background-color:black;background-repeat:no-repeat;background-position:center;background-size:40px 40px;background-image:url(data:image/svg+xml;utf8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEiIHdpZHRoPSIxNzA2LjY2NyIgaGVpZ2h0PSIxNzA2LjY2NyIgdmlld0JveD0iMCAwIDEyODAgMTI4MCI+PHBhdGggZD0iTTE1Ny42MzUgMi45ODRMMTI2MC45NzkgNjQwIDE1Ny42MzUgMTI3Ny4wMTZ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+)}</style><div class="hytPlayerWrapOuter"><div class="hytPlayerWrap"> <iframe width="640" height="360" src="https://www.youtube.com/embed/U8r3VEwD5mg?rel=0&enablejsapi=1" allowFullScreen frameborder="0" ></iframe></div></div> <script>"use strict";document.addEventListener('DOMContentLoaded',function(){if(window.hideYTActivated)return;if(typeof YT==='undefined'){let tag=document.createElement('script');tag.src="https://www.youtube.com/iframe_api";let firstScriptTag=document.getElementsByTagName('script')[0];firstScriptTag.parentNode.insertBefore(tag,firstScriptTag);} let onYouTubeIframeAPIReadyCallbacks=[];for(let playerWrap of document.querySelectorAll(".hytPlayerWrap")){let playerFrame=playerWrap.querySelector("iframe");let onPlayerStateChange=function(event){if(event.data==YT.PlayerState.ENDED){playerWrap.classList.add("ended");}else if(event.data==YT.PlayerState.PAUSED){playerWrap.classList.add("paused");}else if(event.data==YT.PlayerState.PLAYING){playerWrap.classList.remove("ended");playerWrap.classList.remove("paused");}};let player;onYouTubeIframeAPIReadyCallbacks.push(function(){player=new YT.Player(playerFrame,{events:{'onStateChange':onPlayerStateChange}});});playerWrap.addEventListener("click",function(){let playerState=player.getPlayerState();if(playerState==YT.PlayerState.ENDED){player.seekTo(0);}else if(playerState==YT.PlayerState.PAUSED){player.playVideo();}});} window.onYouTubeIframeAPIReady=function(){for(let callback of onYouTubeIframeAPIReadyCallbacks){callback();}};window.hideYTActivated=true;});</script>
</figure>

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