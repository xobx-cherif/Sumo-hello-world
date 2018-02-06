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
     ```xml
     <edges >
     <edge id="1i" from="1" to="0" priority="78" numLanes="3" speed="19.444" />
     <edge id="1o" from="0" to="1" priority="46" numLanes="3" speed="11.111" />

     <edge id="2i" from="2" to="0" priority="78" numLanes="3" speed="19.444" />
     <edge id="2o" from="0" to="2" priority="46" numLanes="3" speed="11.111" />

     <edge id="3i" from="3" to="0" priority="78" numLanes="3" speed="19.444" />
     <edge id="3o" from="0" to="3" priority="46" numLanes="3" speed="11.111" />

     <edge id="4i" from="4" to="0" priority="78" numLanes="3" speed="19.444" />
     <edge id="4o" from="0" to="4" priority="46" numLanes="3" speed="11.111" />

     <edge id="51i" from="1" to="51" priority="78" numLanes="3" speed="19.444" />
     <edge id="51o" from="51" to="1" priority="46" numLanes="3" speed="11.111" />

     <edge id="52i" from="2" to="52" priority="78" numLanes="3" speed="19.444" />
     <edge id="52o" from="52" to="2" priority="46" numLanes="3" speed="11.111" />

     <edge id="53i" from="3" to="53" priority="78" numLanes="3" speed="19.444" />
     <edge id="53o" from="53" to="3" priority="46" numLanes="3" speed="11.111" />

     <edge id="54i" from="4" to="54" priority="78" numLanes="3" speed="19.444" />
     <edge id="54o" from="54" to="4" priority="46" numLanes="3" speed="11.111" />
     </edges>
     ```
    1.3. Now that we have nodes and edges we can call the first SUMO tool to create a network. Make sure NETCONVERT is somewhere in your PATH and call 

    ```shell
    netconvert --node-files=test.nod.xml --edge-files=test.edg.xml --output-file=test.net.xml
    ```

## Generate the route file
(The route definition (<projName>.rou.xml))
Now that we have a net, we still need a car. In SUMO the vehicles have types defining their basic properties such as length, acceleration and deceleration, and maximum speed. Furthermore it needs a so called sigma parameter which introduces some random behavior and is due to the car following model used. Setting it to 0 gives a deterministic car. 
We define a route for our car which simply consists of the edges we defined. 

```xml
<routes>
<vehicles>
<flow id="f11" begin="0" end="10000" from="1i" to="1o" probability="0.1"/>
<flow id="f12" begin="0" end="10000" from="1i" to="2o" probability="0.5"/>
<flow id="f14" begin="0" end="10000" from="1i" to="4o" probability="0.5"/>
<flow id="f21" begin="0" end="10000" from="2i" to="1o" probability="0.5"/>
<flow id="f34" begin="0" end="10000" from="3i" to="4o" probability="0.5"/>
<flow id="f43" begin="0" end="10000" from="4i" to="3o" probability="0.5"/>
</vehicles>
</routes>
```
  

