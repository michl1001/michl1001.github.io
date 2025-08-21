---
layout: page
title: SE(3) LPV-DS for Quadrotor Systems
description: Robust, generalized point-to-point trajectory planning.
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

So, let's say, we want a system that can move the hand from one point in space to another. We _could_ plot out a spline trajectory like so

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/spline.png" title="Exmaple Spline" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

which can then be fed into a PID controller to achieve control of the system.

### Why Bother with Dynamical systems?

Sounds pretty straight forward right? For basic control in a lab or isolated environment, it is! The problems rise when we reach the otuside world - modeling/navigating interaction with a non-static world. For example, say the robot has to hand a box to a person and contend with the human's grip and forcefulness.

- What if the human pushes the robot off course?
- How robot give way to outside forces or remain tightly on the trajectory plan?
- What about moving obstacles and people?

In the system explained above, the robot would likely have to replan it's movement trajectory for every time the enviroment significantly changes - a very inefficient process - or else risk disruptting it's path or, worse, crashing.

This problem prompted the Figeuroa Lab to look into the use of dynamical systems to model the robot's trajectory. Dynamical systems trajectory planners have some nice properties that can guarantee that all possible trajectories will converge to a target destination no matter the starting point.

<div class="row justify-content-sm-right">
    <div class="col-sm mt-6 mt-md-0">
        placeholder
    </div>

    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vector_field.jpg" title="Example DS vector field" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The red line represents the target trajectory, and the arrows represent the directional control from the DS. You can see that the DS guides the robot towards and long the trajectory across the entire space.
</div>

Their particular solution, Linear Parameter Varying Dynamical Systems (LPV-DS), is a system that takes example trajectories and forms a dynamical system model which applies globally the robot's possible states and inputs.

In laymen's terms, given a few demonstrated trajectories, the LPV-DS will generalize the trajectories for the entire environment for a more robust trajectory formulation. This means perturbation recovery is built into how the trajectory planning.

### Why put it on a quadcopter?

Academically, this presented a challenge that would allow us to expand the project to a new area and address it's potential limitations.

Practically, quadcopters may have a lot to benefit from this system. Quadcopters are very susceptible to perturbations and changing environments (wind, objects, etc) and having robustness and adaptivity built into the trajectory planner may give the system more resilience against crashes and misnavigation.

### Our Results

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

<!-- It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %} -->
