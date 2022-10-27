# surfs_up
## Overview:
### Purpose of this analysis
 - In this Analysis we will assist investor W. Avy, to analyze the temperature data for the months of June and December in Oahu,in order to determine if the surf      and ice cream shop business is sustainable year-round.
 - Resources required : 
 
      - Jupyter Notebook Files : [SurfsUp_Challenge IPYNB File](SurfsUp_Challenge.ipynb)
        
      - SQLite Database - [hawaii SQLite File](hawaii.sqlite)

## Results: 
### Deliverable 1 : Determine the Summary Statistics for June
#### Code and Results
      # Import the sqlalchemy extract function.
       from sqlalchemy import extract

      # 1. Write a query that filters the Measurement table to retrieve the temperatures for the month of June. 
      temp_j = session.query(Measurement.tobs).filter(func.strftime("%m", Measurement.date)=="06")
      temp_j
      
      # 2. Convert the June temperatures to a list.
      temp_j = session.query(Measurement.tobs).filter(func.strftime("%m", Measurement.date)=="06").all()
      temp_j
      
      # 3. Create a DataFrame from the list of temperatures for the month of June. 
      temp_june_df = pd.DataFrame(temp_j, columns= ['June Temps'])
      print(temp_june_df)
      
      # 4. Calculate and print out the summary statistics for the June temperature DataFrame.
      temp_june_df.describe()
      
![Test Image](/Resources/June_Temps.png)

### Deliverable 2 : Determine the Summary Statistics for December
#### Code and Results

     # 6. Write a query that filters the Measurement table to retrieve the temperatures for the month of December.
      temp_d = session.query(Measurement.tobs).filter(func.strftime("%m", Measurement.date)=="12")
      temp_d
      
      # 7. Convert the December temperatures to a list.
      temp_d = session.query(Measurement.tobs).filter(func.strftime("%m", Measurement.date)=="12").all()
      temp_d
      
      # 8. Create a DataFrame from the list of temperatures for the month of December. 
      temp_dec_df = pd.DataFrame(temp_d, columns= ['December Temps'])
      temp_dec_df
      
      # 9. Calculate and print out the summary statistics for the Decemeber temperature DataFrame.
      temp_dec_df.describe()

![Test Image](/Resources/December_Temps.png)

### A bulleted list with three major points from the two analysis deliverables. 
   - Temperature in June is more than the temperature in December. Temperature variance can be seen with the difference of few degrees.
   - Average temperature in June is 74.94 degrees F, whereas in December it is slightly lower than in June. Similarly,  Variance of  Min and Max temperature in June      is slightly less than the temperature variance in December. 
   - Based on the Analysis we can predict that from June to December is the best time to attract the maximum number of tourists and thus making the surf shop            business sustainable.
  
## Summary: Provide a high-level summary of the results and two additional queries that you would perform to gather more weather data for June and December.
   - For Ideal surfing ,we should considerate the appropriate amount of precipitation. Therefore, it is really important to anlyze the precipitation levels in Oahu.
   
       results = session.query(Measurement.date, Measurement.prcp).all()
       
       df = pd.DataFrame(results, columns=['date','precipitation'])
       
       df.set_index(df['date'], inplace=True)
   
   - Plot the data for better precision of the analysis:
   
       df.plot()
      
   - Check the active number of stations- Valid enough for the anlysis:
   
       session.query(Measurement.station, func.count(Measurement.station)).\group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
        
