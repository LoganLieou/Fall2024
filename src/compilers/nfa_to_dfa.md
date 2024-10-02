# NFA to DFA

Combine equivalent states for minimized DFA

## Subset Construction Method

1. Construct a transition table to show all reachable states for every state for every single input signal

2. The set of states resulting from every transition function constitutes a new state. Calculate all reachable states for every such state for every input signal.

3. Repeat step 2 until no new states are reachable
