# Copy 5 Files in One Folder on Desktop Named logged_user:

	access_log_short.txt
	hadoop-mapreduce-example-file.txt
	SalesCountryDriver.java
	SalesCountryReducer.java
	SalesMapper.java
	
# Create a Folder named analyzelogs in Home by Following command in Terminal:
	
	mkdir analyzelogs


#Change Permission of that folder and give ownership to the user:

	sudo chmod -R 777 analyzelogs/
	sudo chown -R student analyzelogs/
	
#Copy 5 files From Desktop folder to analyzelogs by following command in Terminal:

	sudo cp /home/student/Desktop/logged_user/* /home/student/analyzelogs/

# Change access_log_short.txt to CSV
	
	Open LibreOffice Excel and follow the Steps:
	Click on FILE > OPEN > SELECT THE FILE > OPEN
	
	* A POP UP WINDOW WILL OPEN
	Select Seperate By Option
		Seperate By [UNMARK ALL OPTION] select Seperate By us (-) only hifan in that field
		
		Change [From Row:] Field from 1 to 2.
		Save as -->  access_log_short.csv
		
# Set Classpath in Terminal by writing:[Change Hadoop Version here it is ]

export CLASSPATH="/usr/local/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-client-core-2.7.5.jar:/usr/local/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-client-common-2.7.5.jar:/usr/local/hadoop/share/hadoop/common/hadoop-common-2.7.5.jar:~/analyzelogs/SalesCountry/*:/usr/local/hadoop/lib/*"
# View Classpath by Following command in terminal:
	 $CLASSPATH
	 
# Compile all Java File by[Go into analyzelog folder by cd /home/student/analyzelogs/]:

	javac -d . SalesMapper.java SalesCountryReducer.java SalesCountryDriver.java
	
# Create Manifest.txt in analyzelogs folder type:
	
	Main-Class: SalesCountry.SalesCountryDriver[Press Enter and Save].
	
# Create Jar File by Using Following Command:

	jar -cfm analyzelog.jar Manifest.text SalesCountry/*.class
	
# create input2000 folder in home and paste the csv file in it.

# START HADOOP by start-all.sh

# Copying input to HDFS file System by following command:

	hdfs dfs -put ~/input2000 /
	
# Then to perform Map and Reduce:
	
	hadoop jar analyzelogs.jar /input2000 /output2000
	
# See the Output by following command:

	hdfs dfs -cat /output2000/part-00000
