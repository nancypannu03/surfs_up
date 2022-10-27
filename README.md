# surfs_up
## Overview of the analysis: 
### Purpose of this analysis
 - In this Analysis we will assist investor W. Avy, to analyze the temperature data for the months of June and December in Oahu,in order to determine if the surf and ice cream shop business is sustainable year-round.
 - Resources required : 
        - Jupyter Notebook Files - [SurfsUp_Challenge IPYNB File](SurfsUp_Challenge.ipynb)
        
        - SQLite Database - [hawaii SQLite File](hawaii.sqlite)

## Results: Provide a bulleted list with three major points from the two analysis deliverables. Use images as support where needed.
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

## Summary: Provide a high-level summary of the results and two additional queries that you would perform to gather more weather data for June and December.
