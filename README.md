# networking


## Transmission Time

### Definition
> The transmission time is the amount of time from the beginning until the end of a message transmission. In the case of a digital message, it is the time from the first bit until the last bit of a message has left the transmitting node.
[Source](https://en.wikipedia.org/wiki/Transmission_time)

### Formula

The packet transmission time in seconds can be obtained from the packet size in bit and the bit rate in bit/s as:
```
Packet transmission time = Packet size / Bit rate
```

### Factors

- Length of packet
- Bandwidth

### Conclusion

```
T1  (Starting Time)
+--------------A                                    B-------+
|01001000100010|                                    |       |
+--------------+                                    +-------+

T2
+--------------A                                    B-------+
|              |01001000100010                      |       |
+--------------+                                    +-------+
```
------------------------------------------------

## Propagation Time

### Definition
> Propagation delay is the time that it takes for a bit to reach from one end of a link to the other. The delay depends on the distance (D) between the sender and the receiver, and the propagation speed (S) of the wave signal. It is calculated as: D/S.
[Source](https://ravindra-utkarsh.medium.com/propagation-delay-in-networking-3ec28f122752)

> The time it takes for the first bit to travel from the sender to the receiver
[Source](https://en.wikipedia.org/wiki/Transmission_time)

### Factors affecting propagation time
- Depends on **propagation speed**,where propagation speed depends on **physical medium** of the link.(in the range of 2 × 10^8 meters/sec for copper wires and 3 × 10^8 for wireless communication)

### Formula

```
Propagation time = Distance / propagation speed
```

### Conclusion

Propagation Time is, how long it takes for a bit to reach B from A.

```
+------A                                    B-------+
|010010|---->--transmission_medium------>---|       |
+------+                                    +-------+
```
---------------------------------

## Packet Delivery Time

### Definition
> The packet delivery time or latency is the time from when the first bit leaves the transmitter until the last is received.
[Source](https://en.wikipedia.org/wiki/Transmission_time)



### Formula

Considering a physical link.

```
Packet delivery time = Transmission time + Propagation delay
```

### Conclusion
```
T1  (Starting Time)
+------A                                    B-------+
|010010|                                    |       |
+------+                                    +-------+

T2
+------A                                    B-------+
|      |010010                              |       |
+------+                                    +-------+

T3(Ending time)
+------A                                    B-------+
|      |                                    |010010 |
+------+                                    +-------+

T2 - T1 = Transmission time
T3 - T2 = Propagation delay
T3 - T1 = Packet delivery time

Therefore, Packet delivery time = Transmission time + Propagation delay
```
--------------------------------
## Round trip time

### Definition
> The round-trip time or ping time is the time from the start of the transmission from the sending node until a response (for example an ACK packet or ping ICMP response) is received at the same node. It is affected by packet delivery time as well as the data processing delay
[Source](https://en.wikipedia.org/wiki/Transmission_time)


### Formula
    Roundtrip time = 2 × Packet delivery time + processing delay

In case of only one physical link, the above expression corresponds to:

    Link roundtrip time = 2 × packet transmission time + 2 × propagation delay + processing delay

If the response packet is very short, the link roundtrip time can be expressed as close to:

    Link roundtrip time ≈ packet transmission time + 2 × propagation delay + processing delay

In theory, we will assume, there is no processing delay,
the Round Trip Time = 2 * Propagation Delay.

<img src="https://d1tcczg8b21j1t.cloudfront.net/strapi-assets/16_What_is_RTT_1_b9a380b57d.png" style="background:white;height:200px;" alt="Transmission time representation"/>

[Source](https://www.stormit.cloud/blog/what-is-round-trip-time-rtt-meaning-calculation/)

### Research paper and article related to round trip time
- https://ieeexplore.ieee.org/abstract/document/6705357
- https://ieeexplore.ieee.org/abstract/document/8319486
- https://ieeexplore.ieee.org/abstract/document/6705357
- https://www.imperva.com/learn/performance/round-trip-time-rtt/

### Problems
- **No reference found**, regading the multiplication of *lenght of packet* by *1-bit round trip time* 

> Note: Transmission of frames, packet or anything, with respect to physical layer, it converts them to electrical pulses, which represent binary data.

```
T1  (Starting Time)
+------A                                    B-------+
|010010|                                    |       |
+------+                                    +-------+

T2
+------A                                    B-------+
|      |010010                              |       |
+------+                                    +-------+

T3(Ending time)
+------A                                    B-------+
|      |                                    |010010 |
+------+                                    +-------+

T2 - T1 = Transmission time
T3 - T2 = Propagation delay
T3 - T1 = Packet delivery time

Therefore, Packet delivery time = Transmission time + Propagation delay
```