
# Level 1 - Write Code

<figure>
    <style>.hytPlayerWrap{display:inline-block;position:relative}.hytPlayerWrap.ended::after{content:"";position:absolute;top:0;left:0;bottom:0;right:0;cursor:pointer;background-color:black;background-repeat:no-repeat;background-position:center;background-size:64px 64px;background-image:url(data:image/svg+xml;utf8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjgiIGhlaWdodD0iMTI4IiB2aWV3Qm94PSIwIDAgNTEwIDUxMCI+PHBhdGggZD0iTTI1NSAxMDJWMEwxMjcuNSAxMjcuNSAyNTUgMjU1VjE1M2M4NC4xNSAwIDE1MyA2OC44NSAxNTMgMTUzcy02OC44NSAxNTMtMTUzIDE1My0xNTMtNjguODUtMTUzLTE1M0g1MWMwIDExMi4yIDkxLjggMjA0IDIwNCAyMDRzMjA0LTkxLjggMjA0LTIwNC05MS44LTIwNC0yMDQtMjA0eiIgZmlsbD0iI0ZGRiIvPjwvc3ZnPg==)}.hytPlayerWrap.paused::after{content:"";position:absolute;top:70px;left:0;bottom:50px;right:0;cursor:pointer;background-color:black;background-repeat:no-repeat;background-position:center;background-size:40px 40px;background-image:url(data:image/svg+xml;utf8;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEiIHdpZHRoPSIxNzA2LjY2NyIgaGVpZ2h0PSIxNzA2LjY2NyIgdmlld0JveD0iMCAwIDEyODAgMTI4MCI+PHBhdGggZD0iTTE1Ny42MzUgMi45ODRMMTI2MC45NzkgNjQwIDE1Ny42MzUgMTI3Ny4wMTZ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+)}</style><div class="hytPlayerWrapOuter"><div class="hytPlayerWrap"> <iframe width="640" height="360" src="https://www.youtube.com/embed/JpiXizx5Sdk?rel=0&enablejsapi=1" allowFullScreen frameborder="0" ></iframe></div></div> <script>"use strict";document.addEventListener('DOMContentLoaded',function(){if(window.hideYTActivated)return;if(typeof YT==='undefined'){let tag=document.createElement('script');tag.src="https://www.youtube.com/iframe_api";let firstScriptTag=document.getElementsByTagName('script')[0];firstScriptTag.parentNode.insertBefore(tag,firstScriptTag);} let onYouTubeIframeAPIReadyCallbacks=[];for(let playerWrap of document.querySelectorAll(".hytPlayerWrap")){let playerFrame=playerWrap.querySelector("iframe");let onPlayerStateChange=function(event){if(event.data==YT.PlayerState.ENDED){playerWrap.classList.add("ended");}else if(event.data==YT.PlayerState.PAUSED){playerWrap.classList.add("paused");}else if(event.data==YT.PlayerState.PLAYING){playerWrap.classList.remove("ended");playerWrap.classList.remove("paused");}};let player;onYouTubeIframeAPIReadyCallbacks.push(function(){player=new YT.Player(playerFrame,{events:{'onStateChange':onPlayerStateChange}});});playerWrap.addEventListener("click",function(){let playerState=player.getPlayerState();if(playerState==YT.PlayerState.ENDED){player.seekTo(0);}else if(playerState==YT.PlayerState.PAUSED){player.playVideo();}});} window.onYouTubeIframeAPIReady=function(){for(let callback of onYouTubeIframeAPIReadyCallbacks){callback();}};window.hideYTActivated=true;});</script>
</figure>

## Resources

### Java Learning Resources

#### Archaic

* [Java Tutorials](https://docs.oracle.com/javase/tutorial/)
* [Java for Complete Beginners](https://www.udemy.com/java-tutorial/)
* [Java Programming and Software Engineering Fundamentals](https://www.coursera.org/specializations/java-programming)

#### Curated Learning

* [CSAwesome, Code.org Curated Courses](https://docs.google.com/document/d/1G6nhE6ZZyG30miTqGP7l75sut6OiOxBa-8xqMm8F-_E)

### WPI Programming Introduction

* [WPILib Documentation](https://docs.wpilib.org/en/stable/docs/zero-to-robot/introduction.html)

## Deliverable

* [Practice Robot Template](https://github.com/FRCTeam4500/PracticeRobotChallengeTemplate)

Clone the Github repository above and open it in VSCode. 

In the `src/main/java/frc/robot/subsystems/` directory, open `TankDriveSubsystem.java`.

Inside is a `TankDriveSubsystem` class and constructor.

Use the resources provided to create the attributes and methods necessary for making a subsystem.

!!! quote "Hint"
    [Build Night #1](/Programming Prophecy/Reflections/Build Night 9.28)

    Looking over the flywheel code will be more helpful than looking at the arm code, since the flywheel uses percent output

Then, in the `src/main/java/frc/robot/commands/` directory, open `TankDriveCommand.java`.

Inside is, once again, a constructor. Fill in the excecute method like the comments say and add [authored documentation](../Programming%20Prophecy/Best%20Practices/AuthoredDocs.md) to everything (All classes and methods with detailed explanations). 

Once finished, bring to one of the leads, and we will get it to a coach. Once approved, you will recieve Level 1 in programming.
