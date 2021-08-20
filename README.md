# I-94-Traffic-Analysis
## Cleaning and visualization of I-94 traffic dataset with intention of determining causes of heavy traffic during the daytime. This project is from [DataQuest](https://github.com/dataquestio) coursework, sharing guided steps to complete the analysis.

The data used to perform this analysis was collected with proximity to MN DoT ATR station 301, located approximately half-way between Minneapolis and Saint Paul. Data was collected between 2012 and 2018. Eastbound traffic data is not collected or analyzed in this project.

More information on the dataset can be found [here](https://archive.ics.uci.edu/ml/datasets/Metro+Interstate+Traffic+Volume).

## Question

What, if any, noteworthy factors contribute to heavy west-bound traffic near station 301 during the daytime?

# Methods

## Daytime vs Nighttime

The first step taken was to determine the hours of the day we consider to be 'daytime'. 

Because the data was collected over the course of 6 years, there is notable daylight fluctuation throughout the timespan of data recording. It may be interesting to find the mean time of day in which the sun rises and sets for each year in 2012-2018 and use the average sunrise/sunset times among those six years.

For the sake of analyzing the data, though, we will favor a less precise measurement and simply consider 7am - 7pm daytime and 7pm - 7am nighttime.

Comparing histograms of daytime traffic and nighttime traffic side-by-side, we can see a much greater frequency of high traffic volume datapoints during the day (mean of 4762 vehicles) in a normal distribution, while the nighttime traffic volume frequency is much lighter (mean of 1785 vehicles) and heavily right skewed, telling us that there is typically much lighter traffic between 7pm-7am.

Because our estimate of daytime and nighttime hours is backed up by the stark difference in traffic volume frequency, we can comfortably omit nighttime data from the dataset at this point.

## Monthly Traffic Volume Frequency

By running a [line plot](https://github.com/quinnrad/I-94-Traffic-Analysis/blob/main/Month%20line%20graph.pdf) of month and mean traffic volume, we can see a clear trend in that traffic volume is reduced during colder months, diving in October from 4900 vehicles to 4400 vehicles in December. The traffic volume makes a steady recovery, plateauing again at 4900 vehicles in March.

There is also a notable dip from June to August, most likely due to school summer break schedules and vacations.

## Days of the Week

Running a similar analysis for days of the week instead of months of the year, we can see a clear trend as we would expect. Traffic volume begins to sharply decrease after Friday (mean 5250 vehicles) reaching a minimum on Sunday (mean 3450 vehicles).

It may also be worth noting that traffic is somewhat lower on Monday (mean 4800 vehicles) compared to other weekdays which remain steady around 5250 vehicles.

Considering weekdays apart from weekends, it was determined that the peak hours for traffic volume on weekdays was at 7am and 4pm, both around 6000 vehicles.
Weekend traffic is very light until around 12pm when it plateaus for the rest of the day around 4000-4500 vehicles.

## Temperature

Using our dataset of daytime traffic, a traffic volume correlation table is produced with respect to our primary temperature relevant data consisting of "temp", "rain_1h", "snow_1h", and "clouds_all".

None of these comparisons yielded noteworthy correlational values with our strongest correlation to traffic volume being "temp" at an alpha value of 0.1283.
A [scatterplot](https://github.com/quinnrad/I-94-Traffic-Analysis/blob/main/Temp%20correlation.pdf) was produced to visualize the lackluster correlation between temp and traffic volume in this location.

## Weather

The last factor we'll look at, our primary weather indicators include descriptions such as "thunderstorm", "snow", "rain", and "smoke".

When grouping traffic volume data by these relevant indicators and taking the mean traffic value under each weather circumstance, [a horizontal bar chart](https://github.com/quinnrad/I-94-Traffic-Analysis/blob/main/Weather%20bars.pdf) depicts the lack of difference each weather indicator has on the traffic volume data.

There are no notable differences in traffic volume between each primary weather indicator, however we also compared weather descriptions, more specific weather indicators, in the same way. This comparison yielded a slightly more noticeable increase in traffic volume for "shower snow" and "light rain and snow", however similar descriptions such as "light shower snow" and "heavy snow" indicated no noteworthy differences.

# Final Words

Westbound I-94 traffic between Minneapolis and Saint Paul during 2012-2018 is primarily affected by month of the year, decreasing from peak in October and returning to peak in March.

Days of the week also play a critical role as expected. Weekdays lead to far more traffic volume, particularly during 7am and 4pm. Nighttime traffic expectedly had the lowest traffic volume as well.

Weather does not seem to play a meaningful role in traffic volume which came as a bit of a surprise to me. I certainly don't like driving fast on snow and ice!
