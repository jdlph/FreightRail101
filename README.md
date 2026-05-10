# FreightRail101
A Tour of Freight Railroad Strategic Planning in North America

## Operating Plan and Trip Planning
In North America, a freight rail operating plan involves three fundamental decisions: blocking, train routing, and train scheduling. With combinatorial complexity in nature, they are usually developed in a sequential way below. 

### Railroad Blocking

Blocking is the first step in strategic planning to consolidate individual traffic flows into blocks. A block, which consists of many railcars (i.e., shipments), can be considered as a group transportation request from an origin to a destination, which are referred to as block origin and block destination. Given a set of shipments and a physical network, the railroad blocking problem is to design a (virtual) blocking service network with the following two sets of decisions. It is usually treated as a network design problem (NDP) and formulated as a mixed-integer problem (MIP).

1. Between which two yards to build a block.
2. The blocking sequence for each shipment.
  
As a shipment requires one or more blocks to reach its last serving yard, the second decision is about how to route a shipment on the designed blocking network via an ordered sequence of interconnected blocks connecting a shipment from its first serving yard to its last serving yard. A waybill may involve two types of classification.
1. Origin classificatio at its first serving yard.
2. (Re)classificationat an itermediate yard.
   
For a shipment, its first serving yard and the last serving yard are generally not its origin and destination. It still has a first-mile trip from its origin to the first serving yard (where it is initially classified into a block) and a last-mile trip from the last serving yard (where the block is declassified into individual shipments) to its final destination. In this sense, the railroad blocking is very similar to the middle mileage planning in logistics. The designed blocks and the corresponding blocking sequences form a blocking plan.

### Train Routing

Given a blocking plan, the next step is to design a set of trains to flow blocks, which also involves two decisions.

1.	Train route as a sequence of links in the physical network, which details the movement of each train from its origin to its destination.
2.	Block-to-train assignment (BTA).
    
Similar to blocking sequence, BTA specifies how a block will flow through trains as a sequence of interconnected train legs, where a train leg corresponds to a train route segment from the block pickup location to the setoff location. Note that they do not have to be the origin or the destination of a train. A block may move through multiple trains. Such a transfer operation is called block swap in railroads or transshipment in logistics. Matching them with the blocking sequence of a shipment will lead to a sequence of train legs which outline how a shipment flows (from its first serving yard to its last serving yard).

As a block is a transportation request requiring pickup and delivery, the train routing problem (for manifest blocks) can be viewed as a variant of the pickup and delivery problem with transshipments (PDP-T). Its outcome as a combination of the foregoing two decisions (train routes and BTAs) is referred to as a routing plan.

### Train Scheduling

A blocking plan and the corresponding routing plan do not have the time component. A scheduling plan, on the other hand, complements a routing plan with train frequency, operating days, and timetabling. It is executed on a weekly basis.

1. Train frequency: how many days to run a train in a week. Note that a train can run at most a time one day up to seven days. 
2. Operating days of week: which days to run a train.
3. Timetabling at each working event location (where blocks are picked up or set off) as arrival time and departure time.

Together, blocking, train routing, and train scheduling define how each waybill traverses the designed service network as a complete itinerary. This integrated planning process is often referred to as **trip planning**.

On the other hand, an itinerary shows where a shipment idles waiting for connections. It is referred to as dwell in railroads. A scheduling plan is generally assessed against total system dwell as measured by $car \cdot days$.

The minimum time required to execute a connection is referred to as the minimum connection time. It will be enforced when establishing the shipment itineraries during trip planning. If the minimum connection time at a location cannot be met, the shipment will select the next available train (as specified by its BTA) to continue its journey. It is generally observed for passengers making transfers from one service line to another in public transit as well.
