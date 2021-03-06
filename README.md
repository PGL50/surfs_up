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

- Minimum temperature in December is only 8 degrees lower than the minimum temp in June
    - June = 64 and December = 56

- Maximum temperature in June is only 2 degrees higher than the maximum temp in December
    - June = 85 and December = 83

- The Interquartile Range (IQR) for June overlaps the IQR for December, as seen in the graph below

     ![IQRs](./Resources/IQR_temp.png) 


<br/>

### Summary

<br/>

#### From the inital temperature analysis of June and December, it is clear that Oahu has a very mild climate year round. The differences in average temp and minimum temp is very small. The maximum temp between June and December only differ by 2 degrees. It looks like a surf and ice cream shop could operate for the entire year. In the chart below it is seen that December has more days in the less than 70 degree range and June has more days in the greater that 75 degrees. But as stated before these temperature ranges are very small and the shop could have mostly mild temps all year long.

<br/>

   ![Hists](./Resources/hist_temp.png) 




#### Another aspect the potential shop owner may want to see is the differences in precipitation for these 2 months of the year. Below are 2 queries run to get the statistics for precipitation for June and December for Oahu.

```Python
# Get the precipitation data for June
date_str = "06"
precip = session.query(Measurement.prcp).\
    filter(func.strftime("%m", Measurement.date) == date_str).all()
juneprecip = list(np.ravel(precip))
juneprecip_df = pd.DataFrame(juneprecip, columns=['June Precipt'])
juneprecip_df.describe()
```

```Python
# Get the precipitation data for December
date_str1 = "12"
precip1 = session.query(Measurement.prcp).\
    filter(func.strftime("%m", Measurement.date) == date_str1).all()
decprecip = list(np.ravel(precip1))
decprecip_df = pd.DataFrame(decprecip, columns=['Dec Precipt'])
decprecip_df.describe()
```

<br/>

#### Here are the precipitation statistics for Oahu for June

<br/>

   ![June Precip](./Resources/june_prec.png) 

<br/>

#### Here are the precipitation statistics for Oahu for December

<br/>

   ![Dec Precip](./Resources/dec_prec.png)    

<br/>

#### December has more tha 50% higher average precipitation than June (.22 vs .14) but the actual amounts are quite low. Below is a graphical comparison of the two months and their precipitaion distributions. The number of days with any precipitation over 0.5 are very small for both months.

<br/>

   ![Hist Precip](./Resources/hist_prec.png)    
   
<br/>

#### As seen with the temperature data the Interquartile Range (IQR) is very similar for June and December for precipitation. 

<br/>

   ![IQR Precip](./Resources/IQR_prec.png)    
   
<br/>

### Conclusion: The surf and ice cream shop will do very well all year round in Oahu based on the weather data for June and December. These months from two different calendar seasons show that Oahu has a very moderate and consistant climate.