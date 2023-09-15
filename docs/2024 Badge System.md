---
hide: 
    - navigation
---

## Welcome Back!

!!! note ""

    First of all, we at the programming team would like to congratulate you on a brand new season of FRC. So glad for all that have joined back from previous years and of course welcome rookies!

    To begin, I will introduce you to a dillema that came from an arguably rushed season in 2023, that being the lack of involvement from members on the team. For this, we apologise greatly. 

    As a method to combat this in the 2024 season, the coaches and leads have come up with a "badging system". In such a system, members of the team are expected to work towards specific milestones in order to be eligible to attend competition.

    <figure markdown style="text-align: left;">
    ## The General Requirements for competition:

    - [ ] Team Registration
    - [ ] Level 1 badge in Scouting
    - [ ] Level 1 badge in Outreach
    - [ ] Exploration - Level 1 badge in an aditional subteam
    - [ ] Specialization - Level 3 badge in one subteam
    </figure>

## Expansive Programming Level Criteria

!!! abstract "Level 1"

    ### 1 - Read Code

    #### Description

    As a programmer, you are proficient in reading and interpreting complex code. In order to pass, one must have the skills to read most of 2023's competition code except boilerplate files and other forms of initialization. You are also not expected to understand most of the logging structure and workflow, however, you should be familiar with it's uses in post-match analysis.

    #### Deliverable

    In order to advance to this state, you must explain selected code to the segments to available leads with accuracy and expand into the roots of why and how the program is created and used.

!!! abstract "Level 2"

    ### 2 - Write Code

    #### Description

    As a programmer, you should be able to write meaningful code in a clean and concice manner provided previous code bases as resources. This includes but is not limited by design patterns such as Singleton and Observer, and industry standard formatting of code. This also includes the use of GitHub for tracking and versioning

    Programming the robot, you must very well understand the robot's control flow. An example of which are the states that the robot can be in throughout the match. Methods extending the LoggedRobot framework are representations of these, providing names such as `teleopInit` or `autonomousInit`.

    This level will be a first extensive deep-dive into Logging and Telemetry. This will include information such as logging subsystems and setting up basic robot simulations.

    #### Deliverable

    In order to advance to this state, you must write clean code that runs successfully on the practice robot. The written code will have to be within specifications determined by subteam leads. This will most likely include movement and may also include a working flywheel shooter or some sort of additional control mechanism.

    This code will need to include logging and possibly IO interface declarations for the logger in order to promote cleaner programming.

    The programmer is expected to provide a detailed runthrough of the program and it's features. If the available leads have questions regarding known topics, the programmer is also expected to answer appropriately. 

!!! danger "Level 3"

    ### 3 - Competition Readiness

    #### Description

    In level 3 of the programming tree, you learn competition skills that are nessesary for the programmer to help in the pits. This includes skills like preparing a radio for competition, imaging radios and rios, debugging erros in code, using software like CTRE Phoenix Tuner and REV Configuration Utility to set up motors and debug `NO ROBOT CODE` errors, and running pre-match system tests.

    You are also to use Advantage Scope (NetworkTables) throughout the process to visualize robot state.

    #### Deliverables

    1. Help with season code base and thoroughly understand how it works.

    2. In order to advance to this state, you must first schedule with one of the programming leads to meet during lunch in Room 38. Once scheduled, a lead will use your code from Level 2 to prepare a testing code base. Once you come to the meeting, you will be expected to demonstrate the use of all above specified software and practices in order to transform provided code into a cleaner and more functional product. (By debugging)

!!! warning "Level 4"

    ### 4 - Revolution

    #### Description

    Level 4 is currently the highest tier of programming to achieve excluding leadership and subteam leads. As such, the requirements are rigorous. As a good programmer, you should be able to write original code that improves the robot. This can be like the inclusion of PathPlanner during 2023 season adding the Logger in 2023 offseason.

    #### Deliverable

    The programmer will provide a branch of season code containing their revolutionary change.