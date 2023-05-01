---
layout: post
categories: posts
title: Senior design
tags: [CAD, CODE]
date-string: 
featured-image: \images\FullMouse.png
---

## Problem

Interacting with computers can be cumbersome and unintuitive. __Hotkeys__ exist to increase workflow, but there are too many to remember and can be a stretch for our fingers.

### Background

Mice purpose built for applications like CAD can result in users working more efficiently. The space mouse for example can lead to a 28% increase in productivity. The mechanism behind this is a reduction in "switching time". According to research done by the Fraunhofer Institute for Industrial Engineering (IAD) and the Technology Assessment Group.
<img src="\images\ProdIncrease.svg" style="width:100%">


## Iteration 1: "Do it in software" 

### Goal  
We can make hotkeys more effective if we can make them less cumbersome to use. What if we put them on the side of a mouse we can get the same productivity gain as the space mouse in other programs? 

### Requirements
These keys need to be dynamic they need to change what key combination is triggered when they're pressed based on what program the user is using so users aren't stuck with keys that only work in one program.

### Results
A few users (Including one of our members so there's bias) have learned to use the dynamic hotkeys and seen a productivity increase.

Other user feedback led us to believe that the learning curve is too steep for end users to see the productivity increase.

### More info

For more info check out the post about this iteration [here](/posts/2020-05-10/MOUSE-SCRIPT.html)

## Iteration 2: "Flatten the learning curve"

### Goal  

People learn based on feedback, can tighten the feedback loop for users when they're using our mouse to try to flatten the learning curve? This would allow users can adopt the mouse into their workflows and become more efficient.

### Summary of features

- Dynamic keys 
    - The keys should be able to be re-mapped dynamically at runtime
- Touch detection 
    - The keys should be able to detect both when they are touched abd when they are pressed
- Compile free configuration
    - The configuration for what keys do in a given configuration should be configurable without recompiling the firmware

## Touchpad Module (This was my module)

In order to enable touch and press detection we investigated how touch detection works. Touch detection is traditionally done with capacitive touch by measuring how much charge a sensing pad can hold.

<div class="img-container">
    <img src="\images\Released.png" style="width:100%">
</div>
<div class="img-container">
    <img src="\images\Touched.png" style="width:100%">
</div>
<div class="img-container">
    <img src="\images\Pressed.png" style="width:100%">
</div>

The images above show how the different states of the button. From left to right they represent the Released touched and pressed states of the buttons. In the released state only a small amount of charge can be pumped into the buttons. With a finger present more charge can be pumped into the button. This is traditional capacitive touch. Finally the new state we came up with was pressed, this happens when the touch pad is tied to VCC. The measurement of held charge is done by measuring how quickly a sensing capacitor is filled. If this sensing pad is tied to VCC the sensing cap will be charged quickly. This allows us to detect "Released" "Touched" and "Pressed" states.

<img src="\images\RawData.png" style="width:100%">

Above is some data we collected from our sensor the purple dots are data collected in the released state the orange is data collected in the touched state and the blue is data collected in the pressed state.

## Mouse firmware (Credit to [Will Scott](https://www.linkedin.com/in/williamnscott/) for this module)

### Input Devices
The mouse firmware is built around the idea of input devices that trigger actions on state transitions.
<img src="\images\InputDeviceConfigs.drawio.svg" style="width:100%">

The configuration for these input devices and their actions can be stored in a json. For example the device with ID one in the figure above would be configured as follows. This format allows us to satisfy the compile free configuration requirement.

    "Device ID 1": {
        "Released":{
            "Pressed":{
                "PressAction":{
                    "Type": "Press",
                    "Key" : "1"
                }
            }
        }
        "Pressed":{
            "Released":{
                "PressAction":{
                    "Type": "Release",
                    "Key" : "1"
                }
            }
        }
    }
    ...

### Actions
Actions are objects that implement a constructor from a json a setup and a teardown method. This allows actions to to be dynamically allocated along when a new configuration is loaded. These actions can do anything the user desires on a key press including running other actions and changing the active configuration. Through these actions we satisfy the "dynamic keys" requirement.  

## Preview Application (This module was all [Justin Cacal](https://www.justincacal.com/))

The preview application interfaces with Windows 10's toast notification. Toast notifications provide a quick display of information to the user that will expire after a certain amount of time. In this case, the information being displayed is the hotkey mapped to on the mouse depending on the application the user is currently working on. When the user enters the "Touched" state of a key press, a signal is sent from the mouse to the computer. After the signal is received, the executable for the notification runs with the key press as the parameter and displays it for the user.

<img src="\images\notificationSS.png" style="width:100%">


## Results

<img src="\images\FullMouse.png" style="width:100%">

### Success

  - Dynamic keys 
      - We are able to re-map keys at runtime based on a new configuration.  
      We do this by implementing a layer change action that modifies the active configuration as a part of the global state of the mouse

  - Touch detection 
      - We can detect all 3 states of our 3 stage buttons
      This works using a traditional touch controller (a TI MSP430FR2676) running custom firmware. We detect the touch and release states as normal. To detect a button press the sense channel is tied to VCC and the charge capacitor is charged very quickly.

  - Compile free configuration
      - We ran into problems reading the JSONs from an SD card on the microcontroller. We were able to test our code on our development machine and without this blocker this feature would've worked.

### Senior design expo

<img src="\images\SeniorDesignExpoECEWinnersSpring23.jpg" style="width:100%">

We presented at the spring 2023 senior design expo and placed 1st in the ECE department.

### WIP

  - Communication over USB
      - We're currently working to get USB communication working reliably