# HiveSQL_Complex_Queries_Project
HiveSQL - Data Science Complex query project

Note - Full pdf attached here for better understanding

# AIM
Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worlwide. Heart failure is a common event caused by CVDs and this dataset contains 12 features that can be used to predict mortality by heart failure. Most cardiovascular diseases can be prevented by addressing behavioural risk factors such as tobacco use, unhealthy diet and obesity, physical inactivity and harmful use of alcohol using population-wide strategies. People with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidaemia or already established disease) need early detection and management.

# Load file, Create table in HiveSQL, Data Insertion HiveSQL in table, Retrive data into Table

1. cd Desktop
2. hadoop fs -mkdir miniproject
3. hadoop fs -put heart_failure_clinical_records_dataset.csv miniproject
4. Hadoop fs -ls miniproject
5. create table bda_project (age INT, anaemia SMALLINT, creatinine_phosphokinase INT, diabetes SMALLINT, ejection_fraction INT, high_blood_pressure SMALLINT, platelets INT, serum_creatinine FLOAT, serum_sodium INT, sex BINARY, smoking SMALLINT, time INT, DEATH_EVENT SMALLINT)
6. row format delimited fields terminated by ‘,’;
7. LOAD DATA LOCAL INPATH ‘Desktop/ heart_failure_clinical_records_dataset.csv’ INTO TABLE bda_project
8. select *from bda_project;

# Operations

1. How many people above the age of 60 are both anaemic and diabetic?< br/>
Query: select count(anaemia)+count(diabetes) from bda_project where Age>60;< br/>
![image](https://user-images.githubusercontent.com/57013059/233916995-b1833525-a78d-4112-8d0a-0d386c386d05.png)< br/>

2. What percentage of women in the dataset do not smoke?< br/>
Query: select count(sex) from bda_project where sex=1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917208-965a43ae-d597-445b-b666-a66073cb6c24.png)< br/>
![image](https://user-images.githubusercontent.com/57013059/233917241-18697f77-f9dd-4713-8b6a-48defd5c8f30.png)< br/>

select (count(sex)/194)*100 from bda_project where smoking=0 AND sex=1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917298-d644712a-9324-4b2f-a6c8-0a5f520235cd.png)< br/>

3. How many men and women below the age of 50 died?< br/>
Query: select count(sex) from bda_project where age<50 AND DEATH_EVENT=1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917389-5ea9cd03-18fe-4a9d-97d9-714facd4612c.png)< br/>

4. How many females have a serum_creatinine level of above 2?< br/>
Query: select count(sex) from bda_project where serum_creatinine > 2 AND sex = 1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917458-62cec1c2-c29d-4d7b-8e31-d64e203ca482.png)< br/>

5. How many men have been called for a follow up in 20 days?< br/>
Query: select count(sex) from bda_project where sex = 0 and time <= 20;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917519-f824de2a-9309-4583-89f2-7f6cc8211861.png)< br/>

6. What percentage of people who weren’t anaemic, or diabetic and did not smoke, died?< br/>
Query: select count(sex) from bda_project;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917595-e80773ce-80fb-43c0-acf4-96b868f29ee2.png)< br/>

select (count(sex)/299)*100 from bda_project where (anaemia=0 OR diabetes=0) AND smoking=0 AND DEATH_EVENT=1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917633-4f2be0a0-1973-4636-9ec3-9aef5cfebca2.png)< br/>

7. What percentage of people who have a high blood pressure did not die?< br/>
Query: select count(sex) from bda_project;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917678-0016dd3b-265c-4680-8557-5f5613519bc5.png)< br/>

select (count(sex)/299)*100 from bda_project where high_blood_pressure=1 AND DEATH_EVENT=0;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917711-debee330-b86e-4f70-8231-8779ac5a4ae2.png)< br/>

8. How many people have a platelet count of lesser than 150000?< br/>
Query: select count(sex) from bda_project where platelets < 150000;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917773-99e9ecec-16b4-431f-aade-cea754654c91.png)< br/>

9. How many men and women have high blood pressure?< br/>
Query: select count(sex) from bda_project where high_blood_pressure=1;< br/>
![image](https://user-images.githubusercontent.com/57013059/233917821-90a0ea7f-ffa6-4819-83fe-397497c0f36f.png)< br/>

