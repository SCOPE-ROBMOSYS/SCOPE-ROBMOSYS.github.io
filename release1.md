---
layout: page
title: Release 1
use-site-title: true
---

This release is simple as it focuses on the first release of the toolchain.
In this scenario the robot must reach a given location. Whenever the battery goes below 20% of its
full capacity, the robot stops and reaches a charging station. It then waits until the battery gets fully charged.
Once the battery is fully charged, the robot resumes the previous navigation.

# Behavior Tree of Release 1

The figure below shows the BT of Release 1.

<p align="center">
<img src="https://user-images.githubusercontent.com/8132627/99839056-68d13180-2b6a-11eb-825d-2e7e8629aee2.png" width="500">
</p>
The BT encodes the following logic:
- The robot checks if the battery level is below 20% of its capacity or if the battery is charging.
- If the battery level is below 20% and it is not already under charge, the robot goes to the charging station.
- If the battery level is charging and the robot is at the charging station, the robot waits until the battery
gets fully charged.
- If the battery level is above 20% and it is not under charge, it goes to the destination.

We made available an OS-level virtualization environment based on [Docker](https://www.docker.com){:target="_blank"} to
reproduce the experiments [here](https://github.com/SCOPE-ROBMOSYS/bt-implementation/tree/release1){:target="_blank"}.
