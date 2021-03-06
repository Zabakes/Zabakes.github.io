---
layout: post
categories: posts
title: DRONE PITT ROCKETRY
tags: [CAD, Pitt Rocketry]
date-string: 
featured-image: \images\drone unfolded.png
---

<center>
<img src="\images\drone unfolded.png" alt="Drone unfolded top">
<img src="\images\drone unfolded btm.png" alt="Drone unfolded bottom">
<img src="\images\drone folded btm.png" alt="Drone folded bottom">
</center>

<left>
I helped design this drone as part of the 2019-2020 Pitt USLI payload team. My focus was on the folding mechanism and chassis. There's no live CAD here cause I used SolidWorks for this design.
</left>

<center>
<H1>FOLDING MECHANISM</H1>
<p>
The drone folds in an X pattern, this allows it to fit inside the 6" ID rocket. In order to unfold the drone pivots around a shaft located at the center of the drone. This could've been accomplished with just straight arms however the bent geometry of the drone allows the width of the drone when folded to be independent of the pan of the drone unfolded. This geometry was driven parametrically. There is a CSV containing parameters for the drone-like it's folded width and span. These parameters are then read in and applied to a sketch by SolidWorks. This sketch has all the necessary constraints to generate arm designs with the desired parameters. The bent arm design allows these two parameters to be independent because it lets SolidWorks change the angle that the arms open and close to, as well as the angle of the bend (in reality one of these can be fixed/dimensioned). Now that the geometry of the arm is defined we can begin to design the folding/locking mechanism. Because drones need to be light we decided on a passive mechanism for unfolding. This is accomplished with wedges on the arms that fall into a potential energy well when they mate with the chassis. This is all held in place by a spring on the top side of the central shaft. This design was inspired by the E3D tool changing system that uses a similar system to lock it's tools into place. The body of this drone was "machined" (it was on an X-carve) out of a 1/4" piece of ABS, this was originally meant to be a prototype but because of events out of our control our season was cut short and it became the final part. The arms themselves were made of carbon fiber also cut on the X-carve. I'm proud of this design, and really enjoyed working with the payload team, shootout to Joe Wright for keeping us on track and organized even though it was most of the members of the team were new. 
</p>

</center>