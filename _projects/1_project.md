---
layout: page
title: SE(3) LPV-DS for Quadrotor Systems
description: Robust, Generalized point to point navigation
img: assets/img/12.jpg
importance: 1
category: work
related_publications: false
---

Over my last semester at my masters, I was on a team that applied Dynamical System Trajectory Planners to Quadcopter path planning to investigate how well the global stability guarantees hold for such systems.

## Background
Consider the Kuka Robot. We can model the robot as a kinematic chain - a hand manipulator attached to many rotational joints. The dynamics of these kinds of robots are *relatively* straight forward (#########if needing many more calculations as multiplications compound#########) so we can create a linear model to operate our dynamics.

So, let's say, we want a system that can move the hand from one point in space to another. We *could* plot out a spline trajectory like so

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

which can then be fed into a PID controller to achieve control of the system.

## Why Bother with Dynamical systems?
Sounds pretty straight forward right? For basic control in a lab or isolated environment, it is! The problems rise when we reach the otuside world - modeling/navigating interaction with a non-static world. For example, say the robot has to hand a box to a person and contend with the human's grip and forcefulness. What if the human pushes the robot? Should the robot give space to the human or remain rigid? What about moving obstacles and people? In traditional robotics, the robot would likely have to replan it's movement trajectory as obstacle occlude which can force the robot to less reactive.

The Figeuroa Lab developed the


## Why put it on a quadcopter?


## How'd it perform?











### Why not Inverse Kinematics?


It's easy to include images in a flexible 3-column grid format.
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

{% endraw %}
