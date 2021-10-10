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

### ETL
Public aircraft tracking data is available from [OpenSky](https://opensky-network.org/). The API provides live position data, as well as historical data when the administrators granted access. As I haven't been granted access, I'm using data from the [Weekly 24 hours of State Vector Data](https://opensky-network.org/data/datasets#d1) dump, which provides all recorded data for Mondays going back about six months. This data is provided as compressed CSV, JSON, or Avro files. Here I'll use the CSV files.

The data amounts to ~60GB of compressed and ~250GB of uncompressed data. Since I'm concerned with only a tiny subset of this, the first step is to cut the data down to the regions of interest, namely a few airports. I do this by created a bounding box of lat/lon coordinates manually. Next, the data is grouped by icao24 and only those with some non-NaN speed/altitude values are taken. It appears that ground vehicles are included in this data, and they always report NaN speend/altitude. Further, the speed/altitude are needed to detect whether an aircraft is taking off or landing (because only takeoffs are considered here). 

Add images here

Next, altitude and speed filters remove any aircraft flying over the region. Then takeoffs are isolated, which is done with another speed filter (applied to the start/end of the data). These steps produce a Multiindex Dataframe, which I save to a parquet file.

## Future Perspectives
