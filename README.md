# Sumo-hello-world
This is a short tutorial to get started with the SUMO simulator.

# Overview

It is not so abuvious to get started with sumo simulator so i decided to make this git as a draft for me.

In SUMO a street network consists of nodes (junctions) and edges (streets connecting the junctions)
The street network could be generated using some files.

After generating the net(street network) file, we still need a car. In SUMO the vehicles have types defining their basic properties such as length,acceleration and deceleration, and maximum speed. Furthermore it needs a so called sigma parameter which introduces some random behavior and is due to the car following model used. Setting it to 0 gives a deterministic car. 
This step consists creating a route file.


# Steps

## Generating the street network file
1. To Generate a network (<projName>.net.xml), to build a network we need some other files like:

    1.1. The nodes file (<projName>.nod.xml)
    All nodes have a location (x- and y-coordinate, describing distance to the origin in meters) and an id for future reference.            
    Thus our simple node file looks as follows 
    ```xml
    <nodes >
    <node id="0" x="0.0" y="0.0" type="traffic_light"/>
    <node id="1" x="-500.0" y="0.0" type="priority"/>
    <node id="2" x="+500.0" y="0.0" type="priority"/>
    <node id="3" x="0.0" y="-500.0" type="priority"/>
    <node id="4" x="0.0" y="+500.0" type="priority"/>
    <node id="51" x="-510.0" y="0.0" type="priority"/>
    <node id="52" x="+510.0" y="0.0" type="priority"/>
    <node id="53" x="0.0" y="-510.0" type="priority"/>
    <node id="54" x="0.0" y="+510.0" type="priority"/> 
    </nodes>
    ```
    1.2. the edges file (<projName>.edg.xml)
    Now we are connect the nodes using the edges. This is as easy as it sounds. We have a source node id, a target node id, and an edge id for future reference. Edges are directed, thus every vehicle travelling this edge will start at the node given in from and end at the node given in to. 

    A route definition (<projName>.rou.xml)

    NETCONVERT

