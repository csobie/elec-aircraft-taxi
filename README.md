# elec-aircraft-taxi

This analysis looks into the potential CO<sub>2</sub> and fuel cost savings for aircraft taxiing by using electric tractors rather than the aircraft turbofans as the means of ground propulsion. Using real air traffic data from OpenSky, a reasonable estimate of these savings is possible.

## Problem Statement

Aircraft travelling from their departure gate to their takeoff position consume a non-negligible quantity of fuel simply for taxiing; a particularly egregious case of this was the Concorde, which consumed up to [two tonnes of fuel while taxiing](http://news.bbc.co.uk/2/hi/business/5195964.stm). Consequently, research into possible means to reduce this fuel consumption and resulting CO<sub>2</sub> emissions is quite active, and a number of studies have compared normal aircraft taxiing with all engines, a subset of engines, or an [Electric Green Taxiing System](https://en.wikipedia.org/wiki/EGTS). These studies tend to take a fixed drive cycle, which limits the usefulness of the results when the cost-quantification of the various options is what would drive decision-making. The analysis in this repository accomplishes the following: 

- quantify fuel consumption and CO<sub>2</sub> emissions of historical aircraft ground movements
- evaluate electric tractor specifications required to meet taxiing requirements
- optimize the tractor fleet size by optimizing the electric tractor dispatch and charging
- evaluate the economic parameters required to make this taxi method conversion fiscally justified

## Topics Covered
This analysis touches on the following topics:

- Discrete event simulation
- Geospatial data analysis
- Graph analysis (shortest path)
- Optimal dispatch heuristics
- Linear Assignment Problem


## Implementation



## Future Perspectives
