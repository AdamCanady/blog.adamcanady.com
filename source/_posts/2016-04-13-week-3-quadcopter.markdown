---
layout: post
title: "Week 3: Quadcopter assembly and testing"
date: 2016-4-12 23:52:33 -0600
comments: true
categories: 
---

## Quadcopter architecture

Our current plan is to use a Naze 32 (rev6, full) flight controller (FC) along with a Raspberry Pi 3 to control the quadcopter. The two devices will communicate via I2C, which contains just two leads connecting the two boards.

The current plan is to inject some code into the Cleanflight firmware which runs on the FC that, at each iteration (50 Hz) of the FC's calculations, outputs all the data over I2C and waits until the iteration time is up (end of the 1/50th of a second) for an overriding instruction from the Raspberry Pi. If the Pi can't make a calculation that fast, or a connection breaks, or has nothing to 'say', then the quadcopter will respond to the precalculated instruction from the FC which is just trying to keep it level. This creates one level of control fail-safe for us, because we can tolerate some faults in the system and still remain airborne in a controlled state.

## Assembly

This iteration, we're using an F250 flamewheel frame. Along with it, we have a power distribution board, the naze32 flight controller, a 5000 mAh battery, and the Turnigy 9X transmitter/receiver. The motors are A2212/13T 1000 KV motors from Wester systems and are controlled by SkyWalker Hobbywing 40A ESCs that have a UBEC (5V @ 3A) that powers the FC and receiver.


## Testing

This is where it gets fun! We put the props on, took the quad outside and took it for a spin to see if the default (very low) PID gain settings worked.
