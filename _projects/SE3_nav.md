---
layout: page
title: SE(3) LPV-DS for Quadrotor Systems
description: Robust, generalized point-to-point trajectory planning
img: assets/img/quad.jpg
importance: 1
category: work
related_publications: false
---

### Synopsis / Contributions

Linear Dynamic Systems are a class of systems where for a given state (position, speed, acceleration, etc.), we can provide some desired action (setting a speed or acceleration). We applied this in the context of trajectory planning for quadrotors in order to achieve lightweight and robust navigation that may be modulated to environmental changes.

As part of a team, I modified our simulator to rapidly test our controller with various flight paths and with perturbations. I also wrote the design modifications required to allow the original LPV-DS systems to be used with a quadrotor's control systems.

### Background

Consider the Kuka Robot. We can model the robot as a kinematic chain - a hand manipulator attached to many rotational joints. The dynamics of these kinds of robots are _relatively_ lightweight so we can create a linear model to operate our dynamics.

So, let's say, we want a system that can move the hand from one point in space to another. We _could_ interpolate a spline trajectory - some set of line equations that are continuous in time - which can then be fed into a PID controller to achieve control of the system.

### Why Bother with Dynamical systems?

Sounds pretty straight forward right? For basic control in a lab or isolated environment, it is! The problems rise when we reach the otuside world - modeling/navigating interaction with a non-static world. For example, say the robot has to hand a box to a person and contend with the human's grip and forcefulness.

- What if the human pushes the robot off course?
- How robot give way to outside forces or remain tightly on the trajectory plan?
- What about moving obstacles and people?

In the system explained above, the robot would likely have to replan it's movement trajectory for every time the enviroment significantly changes - a very inefficient process - or else risk disruptting it's path or, worse, crashing.

<div class="row justify-content-sm-right">
    <div class="col-sm mt-4 mt-md-0">
        This problem prompted the Figeuroa Lab to look into the use of dynamical systems to model the robot's trajectory. Dynamical systems trajectory planners have some nice properties that can guarantee that all possible trajectories will converge to a target destination no matter the starting point.
        <br>
        <br>

        As an example, take a look at the plot. The red line represents the target trajectory, and the arrows represent the directional control from the DS. You can see that the DS guides the robot towards and long the trajectory across the entire space.
        <br>
        <br>

        In theory, a well-fit DS system should be able to produce a global vector field that can generalize most given trajectories.
        <br>
        <br>
    </div>

    <div class="col-sm-6 mt-6 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vector_field.jpg" title="Example DS vector field" class="img-fluid rounded z-depth-1" %}
    </div>

</div>

The Figueroa lab's particular solution, <a href="https://nbfigueroa.github.io/pc-gmm-ds-learning/">Linear Parameter Varying Dynamical Systems (LPV-DS)</a>, is a system that takes example trajectories and forms a dynamical system model which applies globally the robot's possible states and inputs.

In laymen's terms, given a few demonstrated trajectories, the LPV-DS will generalize the trajectories for the entire environment for a more robust trajectory formulation. This means perturbation recovery is built into how the trajectory planning.

### Why put it on a quadcopter?

Academically, this presented a challenge that would allow us to expand the project to a new area and address it's potential limitations. We believed achieving this would require us to leverage orientational information in order to allow the planned trajectories to be more in line with the possible movements of the quadcopter - since quadcopters rely on their orientation for directional motion.

Practically, quadcopters may have a lot to benefit from this system. Quadcopters are very susceptible to perturbations and changing environments (wind, objects, etc) and having robustness and adaptivity built into the trajectory planner may give the system more resilience against crashes and misnavigation.

### Our Results

To describe the results in short, we got our system working by including various modifications to the original SE3 system.

<div class="row justify-content-sm-right">
    <div class="col-sm-5 mt-5 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/SE3_results.png" title="SE3 Results" class="img-fluid rounded z-depth-1" %}
    </div>
    
    <div class="col-sm mt-5 mt-md-0">
        In long, we generated various trajectories using a more traditional quadcopter simulator using splines and normal PID systems (see the repository <a href="https://github.com/utiasDSL/safe-control-gym">here</a>). These trajectories define the ideal paths possible for the quadcopter - in practice, this would be integrating static environmental information into our navigation. These can be seen as the black lines on the figure. You can see that these trajectories don't have to be exact replications and can either diverge or converge before reaching the target destination.
        <br>
        <br>
        The original LPV-DS system was designed for solely x-y-z velocities in mind. While this is enough for the over-actuated, holonomic arm manipulator, we can see our quadcopter struggles with staying on the target trajectories. 
        <br>
        <br>
        To remedy this, we incorporated the Figueroa lab's <a href="https://arxiv.org/abs/2403.16366">SE(3) LPV-DS system</a> which uses orientaiton as part of the input. We can see in the red line that this greatly improved the results of the system but there are still artifacts that cause the quadcopter to drift from the target trajectory.
        <br>
        <br>
        This led us to finally integrate movement direction information as input into the system as per the <a href="https://arxiv.org/abs/2309.02609">Directionality-Aware Mixture Model (DAMM)</a> from the Figueroa Lab. Using this, we allow the trajectories to focus on the flow of the trajectories to gain more accurate reproductions. This is shown in the purple line, which we can see achieves the most accurate results.
        <br>
        <br>
    </div>
    
</div>

### Check Out Our Poster

<embed src="/assets/pdf/MEAM_6230_FINAL_POSTER_S25.pdf" type="application/pdf" width="100%" height="600px" title="SE3_Document">

<!-- Using this system for a quadcopter was a great way to stress test the system. The original design of LPV-DS is designed for arm manipulators which have some nice properties:
- Over-Actuated
- Holonomic
These ultimately mean that a robot manipulator can move arbitrarily in any direction in an instant.

Quadcopters are not any of these which may means using LPV-DS would take some extra work to make viable. -->

<!-- ## How'd it perform?
which can then be fed into a PID controller to achieve control of the system.

## Why Bother with Dynamical systems?
Sounds pretty straight forward right? For basic control in a lab or isolated environment, it is! The problems rise when we reach the otuside world - modeling/navigating interaction with a non-static world. For example, say the robot has to hand a box to a person and contend with the human's grip and forcefulness.
- What if the human pushes the robot off course?
- How robot give way to outside forces or remain tightly on the trajectory plan?
- What about moving obstacles and people?


which can then be fed into a PID controller to achieve control of the system.

In the system explained above, the robot would likely have to replan it's movement trajectory for every time the enviroment significantly changes - a very inefficient process - or else risk disruptting it's path or, worse, crashing.

This problem prompted the Figeuroa Lab to look into the use of dynamical systems to model the robot's trajectory. Dynamical systems trajectory planners have some nice properties that can guarantee that all possible trajectories will converge to a target destination no matter the starting point.

############# insert examples image here ###############33


Quadcopters are not any of these which may means using LPV-DS would take some extra work to make viable. -->

<!-- Using this system for a quadcopter was a great way to stress test the system. The original design of LPV-DS is designed for arm manipulators which have some nice properties:
- Over-Actuated
- Holonomic
These ultimately mean that a robot manipulator can move arbitrarily in any direction in an instant.

Quadcopters are not any of these which may means using LPV-DS would take some extra work to make viable. -->
