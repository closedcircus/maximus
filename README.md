# Maximus
Named after the first circus in the city of Rome, Maximus is our (first) IoT platform.

## Basic Idea
The fundamental idea here is create a software layer above the physical devices where heavy-duty work will be done. This way changes like permissions can be made to an IoT setup without needing to touch the physical devices.

## Components
* Device
* Node
* Master
* Visualizers

#### Device
A device is the actual component that:
* does work
* contains a state
* and can receive commands from an external source

It is most likely a Raspberry PI device but it could easily be anything that does what is stated above.

A device does work. This could be anything, really. It could be turning on a light bulb, measuring the temperature of the room, locking all doors. This work represents the internal working of the device, and is of little concern to Maximus.

A device contains state. For now, state is simply a collection of key-value pairs. For instance, the light bulb device could have the following state:
> STATE: ON  
> RED:   255  
> GREEN: 150  
> BLUE:  0

There are 2 possible ways Maximus could get the state of a device (we'll have to decide which we want or if we want to support both):
1. Pull: Maximus sends a command to the device, and the device replies with its state.
2. Push: the devices sends its state to Maximus

A device can also receive commands from Maximus.

#### Node
* has a store that stores the current state of the underlying device
* runs one or more scripts after every specified interval (or on events) that has access to the state variables
* publishes (and subscribes to) events // this facilitates cross-node comms
* nodes may make requests to other nodes
* hooks that subscribe to events
* how do you connect a node to a device?

#### Master
* hooks that subscribe to events (without creating a node for such nodes)

This is designed to facilitate cross-node communication. For instance, assuming we want a light bulb to go off when the temperature in the room is above 20<sup>o</sup>C, we need to facilitate communication between the light bulb device and the thermometer device. While
