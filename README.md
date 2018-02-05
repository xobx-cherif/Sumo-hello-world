# Sumo-hello-world
This is a short tutorial to get started with the SUMO simulator.

#Overview

It is not so abuvious to get started with sumo simulator so i decided to make this git as a draft for me.

In SUMO a street network consists of nodes (junctions) and edges (streets connecting the junctions)
The street network could be generated using some files.

After generating the net(street network) file, we still need a car. In SUMO the vehicles have types defining their basic properties such as length,
acceleration and deceleration, and maximum speed. Furthermore it needs a so called sigma parameter which introduces some random
behavior and is due to the car following model used. Setting it to 0 gives a deterministic car. 
    A network (<projName>.net.xml).
        To build a network we need some other files like.
            <projName>.nod.xml

            <projName>.edg.xml

    A route definition (<projName>.rou.xml)

    NETCONVERT

