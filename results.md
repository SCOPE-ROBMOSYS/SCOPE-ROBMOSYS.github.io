---
layout: page
title: Results
use-site-title: true
---

The figure below depicts the toolchain developed and its actors in the [RobMoSys's Ecosystem Organization](https://robmosys.eu/wiki/general_principles:ecosystem){:target="_blank"}:

![toolchain](https://user-images.githubusercontent.com/8132627/99809156-2c89db00-2b42-11eb-8b08-1d866733987d.png)


The [Behavior Developer](https://robmosys.eu/wiki/general_principles:ecosystem:roles:behavior_developer){:target="_blank"} implements the task-plots that encode the robotic system orchestration at runtime.
The [Component Supplier](https://robmosys.eu/wiki/general_principles:ecosystem:roles:component_supplier){:target="_blank"} implements the single component and it also develops the skills that orchestrate components.
The [System Builder](https://robmosys.eu/wiki/general_principles:ecosystem:roles:system_builder){:target="_blank"} then selects
such components to realize the services required by the robotic system.
An Interface Definition Language (IDL) defines the component coordination interface between the task plot and skills. The Service Designer creates such IDLs, while the Behavior Developer and the Component Supplier use them.


The toolchain allows to describe a [task plot](https://robmosys.eu/wiki-sn-04/modeling:metamodels:behavior){:target="_blank"} only in terms of BT, using the [Groot](https://github.com/BehaviorTree/Groot){:target="_blank"}
 XML format, the skills only in terms of Finite State Machines (FSMs), using the W2C's [scxml format](https://www.w3.org/TR/scxml/), and the communication interfaces via [Thrift IDL](http://www.yarp.it/git-master/thrift_tutorial.html){:target="_blank"}. From these descriptions all the code is automatically generated, with the exception of the code implementing the components, which we assume are already existing. In this specific implementation, we use the YARP middleware and generate YARP specific code, however, nothing prevents to generate code for other runtime environments, provided they implement the Query communication pattern.


A user defines the BT in form of an XML file, created manually or using a  Graphical User Interface (e.g. [Groot](https://github.com/BehaviorTree/Groot){:target="_blank"} or [Papyrus4Robotics](https://www.eclipse.org/papyrus/components/robotics/)).
The BT is then interpreted and executed by the [BehaviorTree.CPP engine](https://github.com/BehaviorTree/BehaviorTree.CPP){:target="_blank"}. The leaf nodes of the BT, that represents [skills](https://robmosys.eu/wiki-sn-04/modeling:metamodels:behavior){:target="_blank"}, are implemented as FSMs. The user defines them using the W2C's scxml.

The [qtscxml compiler](https://doc.qt.io/qt-5/qtscxml-overview.html) interprets and executes the skills' FSMs. Each FSM may send requests to different components to compute the return status to be sent to the parent node in the BT. An IDL defines the communication between BT and FSMs, and  between FSMs and components. It is implemented via the [YARP Thirft](http://www.yarp.it/git-master/thrift_tutorial.html){:target="_blank"} Remote Procedure Calls, which is synchronous and follows the [RobMoSys Query communication pattern](https://robmosys.eu/wiki/modeling:metamodels:commpattern){:target="_blank"}. The components, on the other hand, can communicate with each other using any of the [RobMoSys's communication patterns](https://robmosys.eu/wiki/modeling:metamodels:commpattern){:target="_blank"}.
