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

<img width="1171" height="663" alt="image" src="https://github.com/user-attachments/assets/edf9dc61-e873-44d3-82ac-75c32892480d" />

As we can see, the graph above displays the degradation values along with their frequency. The trend observed is rather particular, as it features two distinct peaks. The reason is that using two different tyre compounds results in two separate groups. Since we are unable to intervene or normalize these data due to the lack of a unified distribution, it becomes necessary to divide the data based on the type of compound used

<img width="541" height="715" alt="image" src="https://github.com/user-attachments/assets/d1aa23b4-5175-4289-b9ad-98e7366b5a18" />

The values considered for formulating the hypothesis were determined by calculating the average of the operating range for each tyre compound:

Hard tyres: [0.05; 0.07] → average = 0.06

Medium tyres: [0.07; 0.10] → average = 0.085

Given the presence of a left-tailed distribution, we define our null hypothesis as H₀: degradation ≥ 0.06 for hard tyres, and analogously for medium tyres. Consequently, if a driver's data fails to reject the null hypothesis, we interpret this as an indication of higher degradation. Conversely, rejecting the null hypothesis suggests lower degradation.

Our hypothesis is that stronger drivers tend to exhibit lower degradation levels, and we extend this expectation to the teams as well. To evaluate team performance, we assess the outcome of four hypothesis tests—two for each driver (one for each compound). A team is considered strong if a significant number of these tests result in the rejection of the null hypothesis, indicating lower degradation and, by extension, better tyre management.

### Confidence Interval
<img width="907" height="562" alt="image" src="https://github.com/user-attachments/assets/2f9e67f2-70db-45e7-90a6-db44db70fcc3" />

These charts display the 90% confidence intervals for lap-by-lap degradation on medium and hard compounds for each driver. The dashed vertical lines represent the expected degradation for each compound, based on its operating range (≈ 0.085 for medium, ≈ 0.060 for hard). On the medium tire, drivers like ALO, OCO, STR, SAI, RUS, LEC, BOT, GAS, and RIC show degradation below or near the expected range, suggesting efficient tire use. MAG, PER, and PIA are close to the benchmark, while NOR, HAM, and VER exceed it, indicating higher wear. On the hard tire, drivers such as ALO, OCO, STR, SAI, LEC, BOT, GAS, RUS, and COL perform better than expected, whereas MAG, HUL, HAM, RIC, and PER align more closely with the compound's operating range. PIA, NOR, and VER degrade more quickly than expected. Narrow intervals (e.g., BOT, LEC, STR) suggest consistency, while wider ones (e.g., GAS or RIC on mediums) may result from fewer laps or variable stint conditions.

## Conclusion
The objective of this study was to analyze the degradation of Formula 1 tires during a race, employing a statistical framework including hypothesis testing to characterize their behavior accurately. The data obtained after processing largely aligned with our expectations, as the majority of values fell within the predetermined reference intervals, with only a few outliers excluded from the analysis. These outliers were mainly attributable to anomalies in driver behavior, which influenced the segmentation of the circuit and data sections, or to potential inaccuracies in the calculations estimating tire degradation.

The degradation results proved particularly insightful. An examination of the 'Degradation per Lap - All Drivers' graph revealed significant variation among drivers in terms of tire wear patterns. This heterogeneity is primarily explained by the differences in tire compounds used—specifically, hard and medium compounds—necessitating the separation of the dataset into two distinct categories to account for these variations adequately.

Furthermore, the outcomes of the hypothesis tests yielded several compelling observations. Notably, drivers and teams traditionally regarded as top performers exhibited greater tire degradation compared to their competitors, but this came with the advantage of faster lap times. This suggests a trade-off between speed and tire longevity, where the most competitive drivers push their tires harder to achieve superior performance. However, an exception to this trend was observed with Ferrari drivers (Sainz and Leclerc), who demonstrated relatively low tire degradation despite maintaining high speeds.

This disparity can be largely attributed to differences in car design and engineering philosophies. Each Formula 1 team develops a uniquely configured vehicle, resulting in distinct driving characteristics and tire wear profiles. For example, Red Bull cars are generally characterized by a stiffer chassis setup, necessitating a more aggressive driving style that the degradation model predicts as causing higher tire wear. Yet, in practice, the actual tire degradation tends to be lower than the model suggests, likely due to nuanced differences in suspension setups and aerodynamic configurations. Conversely, Ferrari has engineered a car for this race that prioritizes maintaining consistent lap times at slightly lower peak speeds, thereby achieving a more balanced compromise between tire degradation and velocity. This balance appears to be an effective strategy, enabling competitive race pace without excessively compromising tire durability.

The linear regression analysis further supports the robustness of the proposed model, demonstrating a close alignment between predicted and observed data. This strong correlation indicates that the model effectively captures the degradation behavior of the tires. Additionally, the degradation levels predicted by the model correspond closely with real-world scenarios, notably aligning with the tire wear threshold (reference value of 1.5) that typically triggers pit stops during races. This concurrence validates the practical applicability of the model and its potential utility for strategic race planning.

Future improvements could involve extending this type of analysis to multiple circuits, which would allow for the development of a broader behavioral profile for each driver. By studying their performance across various tracks, it would be possible to model and characterize individual driving styles more accurately. This could lead to the creation of predictive behavioral models tailored to both driver and car characteristics.

Naturally, such analyses would benefit significantly from having access to comprehensive real-time telemetry and sensor data directly from the vehicles. This would allow for the development of a more refined and precise model, increasing the accuracy of predictions regarding tire wear and performance.

Another promising direction for future work would be implementing real-time lap-by-lap analysis to provide predictive feedback to drivers and race engineers. This system could suggest the most optimal timing for pit stops or recommend adjustments in driving behavior in response to emerging degradation patterns. Such predictive tools could be integrated into live strategy systems, enhancing decision-making under dynamic race conditions.

Overall, this project not only demonstrates the potential of statistical modeling in motorsport but also opens the door to data-driven performance optimization in real time.
