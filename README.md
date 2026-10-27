# When do people rent Citi Bikes at E 2 St & Avenue B?

Example project for URP 6295: Urban Data Structure Basics.

## 1. Urban question
When do people start bike-share trips at one Manhattan Citi Bike station, and how does weekday use differ from weekend use? The answer can tell the operator when the station needs bikes restocked.

## 2. Data
- **Source:** [Citi Bike System Data](https://citibikenyc.com/system-data), August 2015. The subset used here (trips that started at station 301, E 2 St & Avenue B) comes from [introduction_to_ml_with_python](https://github.com/amueller/introduction_to_ml_with_python/blob/master/data/citibike.csv).
- **Type:** tabular time series. Each row is one trip with its start time, end time, duration, start and end stations, and user type.
- **Size:** 4,212 trips, 15 columns, Aug 1-31, 2015. Stored in `data/citibike.csv`.

## 3. Input and output
**Input:** trip records, one row per trip (first 5 of 4,212 rows shown).

![input](input_example.png)

**Output:** average number of trips started in each hour of the day, for weekdays and weekends.

![output](output_example.png)

## 4. First working code
`analysis.ipynb` loads the CSV with Pandas, counts trips per hour for each day, averages weekdays and weekends separately, and saves both images above.

To run it:
```
pip install pandas matplotlib jupyter
jupyter notebook analysis.ipynb
```

First result: weekday trips peak at 7-8 am and again at 6 pm (commuting). Weekend trips peak around noon.

## 5. Plan
**Next steps**
- Clean the data: some trips last over 30 hours. Decide on a cutoff and remove those trips.
- Compare subscribers (members) with customers (day-pass users).
- Add more stations or months from the Citi Bike System Data site.

**How I will check the results**
- The hourly counts must add up to the total number of trips (4,212). This check is in the notebook.
- Count the trips for one day by hand and compare with the notebook's numbers for that day.
