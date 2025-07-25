# Project Topic: Degradation of F1 wheels
### Project Overview
This project aims to give insight to the tyre degradation over the different laps in a Grand Prix. This project would help to analyse, using statistical tools, the lap-by-lap degradation of a car’s tires during a Grand Prix, based on telemetry data segmented by track sectors and collected for each lap. Using the available data, tire wear will be measured and analyzed. The focus of the analysis is on applying hypothesis testing, confidence intervals, and linear regression to interpret tire behavior over time and to identify statistically significant relationships between variables. The goal is to describe the phenomenon from a statistical perspective and support the technical evaluation with quantitative evidence.

### Data Source
The dataset is sourced from the official FastF1 Python library, which provides access to detailed Formula 1 telemetry and timing data. The data is extracted using a custom Abstract Data Type (ADT) designed specifically for this project.

### Tools Used
- Python [Download Here](https://www.python.org/downloads/)

### Data Cleanup
To obtain the data, I  utilized the FastF1 library. This is a Python library developed by the community and Formula 1 enthusiasts, which provides comprehensive information related to Formula 1 across all Grand Prix sessions. In addition to offering detailed telemetry data such as braking, throttle, speed, and more, it also includes radio communications, ambient temperature, pit stop data, and various other metrics. The use of this library proved to be the most accurate method for obtaining official data in a highly precise manner, allowing us to minimize the risk of errors as much as possible.

### Exploratory Data Analysis
After collecting all the data, I conducted a thorough analysis from multiple perspectives in order to explore various aspects beyond our initial assumptions. The first step was to visualize the performance trends of all drivers within a single plot, allowing me to observe the overall dataset in a unified and comparative way. The primary data analyzed consisted of the relationship between lap number and tire degradation (lap_degradation), which provided a clear view of how tire wear evolved over time for each driver.

<img width="1154" height="657" alt="image" src="https://github.com/user-attachments/assets/44b5de02-1b4d-4b94-a140-79d9e3dacf12" />

<img width="1166" height="664" alt="image" src="https://github.com/user-attachments/assets/682b4018-011c-4cbd-8ca3-bff151c44687" />

The graph above represents a scatter plot showing the relationship between lap number and degradation for each driver throughout the race. This visualization highlights the performance differences between medium and hard tires.

In addition, another key area can be observed between laps 20 and 31, highlighted in the grey rectangle. Within this segment, it is evident that almost all drivers are running on hard compound tires. This observation aligns with race strategy logic: medium tires tend to wear out faster than harder compounds and thus require an earlier pit stop. As a result, drivers who started on medium tires were forced to switch to hard tires before lap 20.

Conversely, drivers who began the race on hard tires did not yet need to pit during this phase, as the degradation rate of hard compounds is lower, making a tire change unnecessary at that stage of the race.

