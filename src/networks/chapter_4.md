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


