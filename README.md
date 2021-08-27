# Overview of the Oahu Surfs Up Analysis

### A potential surf and ice cream shop owner in Oahu wants information about the weather in June and December to make decisions about opening a shop. The analyses include data from an sqlite database read in using SQLAlchemy. Python in combination with Pandas will retrieve the weather information for June and December. Additional queries are performed to gather even more information for and informed decision.

<br/>

## Deliverable 1: Determine the Summary Statistics for **June** 

<br/>

![June temps](./Resources/June_temps.png) 

<br/>

#### Here is the Python code to generate the June temp statistics
```Python
date_str = "06"
temps = session.query(Measurement.tobs).\
    filter(func.strftime("%m", Measurement.date) == date_str).all()
	
junetemps = list(np.ravel(temps))

junetemps_df = pd.DataFrame(junetemps, columns=['June Temps'])
	
junetemps_df.describe()
```

<br/>

## Deliverable 2: Determine the Summary Statistics for **December** 

<br/>

![Dec temps](./Resources/Dec_temps.png) 

<br/>

#### Here is the Python code to generate the December temp statistics
```Python
date_str1 = "12"
temps1 = session.query(Measurement.tobs).\
    filter(func.strftime("%m", Measurement.date) == date_str1).all()
	
dectemps = list(np.ravel(temps1))

dectemps_df = pd.DataFrame(dectemps, columns=['December Temps'])
	
dectemps_df.describe()
```

<br/>

## Deliverable 3: Results and Summary

<br/>

### Results
- Mean temperature is not much higher in June vs December (indicating a very moderate climate) 
    - June = 74.9 and December = 71.0

- Mean temperature is not much higher in June vs December (indicating a very moderate climate) 
    - June = 74.9 and December = 71.0