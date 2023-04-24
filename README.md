# HiveSQL_Complex_Queries_Project
HiveSQL - Data Science Complex query project

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

1. select count(anaemia)+count(diabetes) from bda_project where Age>60;
2. select count(sex) from bda_project where sex=1;
3. select (count(sex)/194)*100 from bda_project where smoking=0 AND sex=1;
4. select count(sex) from bda_project where age<50 AND DEATH_EVENT=1;
5. select count(sex) from bda_project where serum_creatinine > 2 AND sex = 1;
6. select count(sex) from bda_project where sex = 0 and time <= 20;
7. select count(sex) from bda_project;
8. select (count(sex)/299)*100 from bda_project where (anaemia=0 OR diabetes=0) AND smoking=0 AND DEATH_EVENT=1;
9. select count(sex) from bda_project;
10. select (count(sex)/299)*100 from bda_project where high_blood_pressure=1 AND DEATH_EVENT=0;
11. select count(sex) from bda_project where platelets < 150000;
12. select count(sex) from bda_project where high_blood_pressure=1;
