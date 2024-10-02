# Medium Access Control Layer

## MAC Sub Layer

- Broadcast medium, if a user puts a signal in everyone receives the signal
- Key issue: who gets to use the channel
    - In case there is competition
    - How to manage without central coordination?
- MAC protocols for managing access to the broadcast channel
- Why "Sub Layer"? is technically a part of the data link layer but the problem is specific enough it justifies the abstraction

## Channel Allocation Problem

- How do you allocate the channel among competing users
- Static schemes FDM N users bandwidth is divided into equal sized parts there is no interference, this is viable for small number of users
- FDM has fairly poor performance, $\mu{}C = \frac{C}{\frac{1}{\mu{}}}$ channel rate over frame length in bits
- The average delay is $T = \frac{1}{\mu{}C - \lambda{}}$ since you are competing with others the average delay is actually double what you would expect, there's more math here to show how poor the FDM performance is but it's probably irrelevant
- TDM also has poor performance this is something to do with the bandwidth not being optimally utilized there's math here will worry about it later

## Dynamic Schemes

**Station Model** N independent stations each has a program that generates
frames $\lambda{}\delta{}t$ is the probability a frame is generated in the
interval $\lambda{}t$ ooo see how this is a poisson process wow.

**Observable Collision** if the transmission of two frames overlap there is a
collision, all terminals can detect collisions, collision detection is hard due
to a possibly large delay

**Time** time can either be continuous or slotted, with slotted time a frame
can only be sent at a certain time, i.e. if a frame is generated between two
time slots we will await for the next time

**Channel Usage** carrier sense implies that terminals can sense if a cannel is
already in use before transmitting. No carrier sense implies that terminals
cannot sense the channel and will transmit regardless, later terminals may be
able to tell if a collision occurs.

## Pure Aloha

The idea behind Aloha is that you allow users to send data whenever they have
data to send and that there will of course be collisions, there is someway the
station will realize that the frame has collided then wait a *random* amount of
time before resending the frame

**Efficiency** what fraction of all transmitted frames escape collision under
chaotic circumstances (throughput). The actual number is poisson distributed
with a mean value of $N$ frames per frame time there are $k$ retransmission
attempts also poisson distributed with mean $G$ hence we can calculate the
throughput. The probability of $k$ frames:
$$
Pr[k] = \frac{G^ke^{-G}}{k!}
$$
The probability of 0 frames is $e^{-G}$ using $S = GP_0$ we find that
$$
S = Ge^{-2G}
$$
Here we can use MLE to find that $G = 0.5$ and $S = 1/2e$ hence the maximum
throughput implies only 18% of frames make it through

## Slotted Aloha

Time is divided into slots. The throughput for this is defined $S = Ge^{-G}$

an example here is that given that 10% of the time channels are idle find the
throughput.

$P_0 = e^-G$ we know $P_0 = 0.1$ then solve for $G$ which gives you the
throughput in a slotted aloha hence, $S = 0.23$ solving for $G$ is $> 1$ so the
channel is overloaded

## Timing Issues...

Not sure what's going on in this slide I can just go back and look at this fuck

## Carrier Sense Multiple Access Protocol


## Collision Free Protocols

Goal: contention is resolved without collisions

**Bit Map Protocol** each contention period has exactly `N` slots if terminal
`i` has a frame to transmit it sends a 1 in the ith slot after the contention
period every terminal will know who will transmit and when this can be viewed
as a sort of reservation.

**Reservation Protocols** in this protocol we reserve time slots in advance so
we know who is transmitting what and for how long. Drawbacks; if terminal
become ready after transmit slot has passed then it must wait until the next
contention period this could cause significant delay

- Approximate performance for this protocol you have to wait an average of $\frac{N}{2}$ bit slots for the current scan to finish and another $N$ bit slots for another full scan to complete.

**Binary Countdown** High numbered stations have higher priority can be good or
bad depending on the context, can be equalized by circularly shifting hte
address bits. (idk what this is go take notes on this ig)

## Limited Contention Protocols

Combining the best properties of contention and collision free protocols, at low
load we use contention to provide low delay, i.e. we allow for collisions at low
loads and at high loads we use collision-free to provide channel efficiency.

### Adaptive Tree Walk Protocols

- example of limited contention protocol

## What we've Learned

- Aloha Protocol
- CSMA
- Collision-Free
- Limited-Contention
- MAC in Wireless Networks