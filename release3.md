---
layout: page
title: Release 3
use-site-title: true
---

This release is similar to the one we developed for the [Release 2](release2.md){:target="_blank"} with the main difference in the development of the generated runtime monitors.

# Behavior Tree of Release 3


The figure below shows the BT of Scenario 3.

<p align="center">
<img src="https://user-images.githubusercontent.com/8132627/99838997-4fc88080-2b6a-11eb-9d60-6cb3e4da68fa.png" width="500">
</p>



The BT encodes the following logic:

- The robot checks if the battery level is below 30% of its capacity or if the battery is under charge.
- If the battery level is below 30% and it is not already under charge, the robot goes to the charging station.
- If the battery is under charge and the robot is at the charging station, the robot waits until the battery gets fully charged.
- If the battery level is above 30% and it is not under charge, it performs the main task.

The main task is:
 - If there are no objects in the robot's hand, the robot goes to the user to fetch an object.
 - If there is an object in the robot 's hand, the robot goes to a predefined destination.

# Execution of Release 3

 The video below shows the execution of Release 3.  We present three scenarios, a nominal one (with no property violation), one with a safety property violation, and one with a response property violation.
<p align="center">
  <iframe width="580" height="315" src="https://www.youtube.com/embed/VzwVpr9RR0E" frameborder="0" allowfullscreen></iframe>
</p>
