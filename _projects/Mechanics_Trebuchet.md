---
layout: page
title: Mapping Trebuchet Trajectories with Lagrangians
description: Using Lagrangian Solvers to yield trajectories
img: assets/img/physics_trebuchet_1.png
importance: 20
category: Research
related_publications: false
---

#### December 2021

### Synopsis 

<!-- I used to be a Physics Minor at my undergrad. One of my early projects was to model the dynamics of a trebuchet in order to model projectile trajectories. The trebuchet is a projectile launcher that uses a counter weight to induce rotational motion of a double inverted pendulum. For reference, see [here](link to trebuchet video). -->

Besides being a good exercise in mechanics, the double inverted pendulum happens to be the same model used for robotic limbs (kinematic chains).


### Why a Trebuchet?

<!-- The trebuchet is a sling attached to a weighted pendulum designed launch a projectile across a long distance. While this may seem like a random model, it just so happens that an equivalent model for this trebuchet is the double inverted pendulum.

The inverted pendulum is a well known model in robotics for experimenting with control systems - in part, because the system is also models similar dynamics to arms and legs.  -->

A trebuchet consists of a sling attached to a weighted pendulum that is designed to launch a projectile over long distances. Although this may seem like an unusual system to study, its dynamics can be modeled similarly to a human throwing arm.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Double_inverted_pendulum.svg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

Consider the double inverted pendulum - a well-known model in robotics and control theory, often used to develop and test control systems. It is particularly valuable because its dynamics resemble those of human limbs, such as arms and legs, making it a useful framework for studying balance, motion, and control.

Obviously, the arms on a trebuchet don't quite match a human arm but the joint placements mean that the dynamics and calculations are related which we will see later.


### What's a Lagrangian?

In layman's terms, Lagrangian Mechanics writes out all the relevant dynamics of a system in terms of the energy - particularly as `$$L = T - U$$` where `$$T$$` is the kinetic engery and `$$P$$` is the potential energy. By taking [certian derivatives and integrals](Link to later detail about action shaping), we can establish a system of equations which solves for the final equations of motion.

This may seem really basic but there are a lot of nice properties we get by doing this - because this quantity is a unit of energy, it also happens to be scalar - which means that we can cherry pick coordinate units to make the math easier so long as all aspects of the motion and potential energy are described.


### Putting Things Together


### Our Results