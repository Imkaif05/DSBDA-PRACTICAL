Step 1 . Use these 4 files

	access_log_short.txt
	SalesCountryDriver.java
	SalesCountryReducer.java
	SalesMapper.java
	
	
Step 2 :convert access_log_short.txt to csv file 
# Change access_log_short.txt to CSV
	
	Open LibreOffice Excel and follow the Steps:
	Click on FILE > OPEN > SELECT THE FILE > OPEN
	
	* A POP UP WINDOW WILL OPEN
	Select Seperate By Option
		Seperate By [UNMARK ALL OPTION] select Seperate By us (-) only hifan in that field
		
		Change [From Row:] Field from 1 to 2.
		Save as -->  access_log_short.csv  //done
	
	
Step 3 :Go to Eclipse 
	  create Java Project 
	   Add Package with name "SalesCountry"
	   in this package create new 3 java files with name 	 	SalesMapper,SalesCountryDriver,SalesCountryReducer (copy or write code)
	   
	   Add 3 jars files through buildpath-->configure Build Path-->Libraries-->add external Jar file	 
	   	1. hadoop/mapreduce/hadoop-mapreduce-client-core-2.7.5.jar	 
	   	2. hadoop/mapreduce/hadoop-mapreduce-client-common-2.7.5.jar
	   	3. hadoop/common/hadoop-common-2.7.5.jar
	  
Step 4: Creation of Jar file with Eclipse 	   	
	Export-->Java-->Jar files-->assign Name to jar files-->Browse Main class file-->Finish

	
# create input2000 folder in home and paste the csv file in it.

# START HADOOP by start-all.sh

# Copying input to HDFS file System by following command:

	hdfs dfs -put ~/input2000 /
	
# Then to perform Map and Reduce:
	
	hadoop jar analyzelogs.jar /input2000 /output2000
	
# See the Output by following command:

	hdfs dfs -cat /output2000/part-00000
