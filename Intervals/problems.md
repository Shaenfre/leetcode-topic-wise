## Non overlapping intervals

- sort the events with respect to start time
- iterate through them
- if at any point start of current event is less than end of previous event we can pick only one event out of them
- we will greedily pick the event which ends early so that there is a greater chance of next event also being picked up