# Maximus
Named after the first circus in the city of Rome, Maximus is our (first) IoT platform.

## Basic Idea
The fundamental idea here is create a software layer above the physical devices where heavy-duty work will be done. This way changes like permissions can be made to an IoT setup without needing to touch the physical devices.

## Components
* Device
* Node
* Visualizers

#### Device
A device is the actual component that:
* does work
* contains a state
* and can receive actions from an external source

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

#### Node
