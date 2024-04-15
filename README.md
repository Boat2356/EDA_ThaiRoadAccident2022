# Analyze accident data in Thailand using Exploratory Data Analysis (EDA) methods.
## The origin and significance
Road accidents in Thailand can occur anywhere, at any time, and involve people of all ages and genders. They can cause a great deal of property damage and casualties as well as economic system disruption. Several elements contribute to accidents. From what has been stated thus far, it appears that the publisher is interested in using exploratory data analysis to examine the relationships between the variables when analyzing road accident data in Thailand. The data will then be processed into easily readable graphs or other formats to provide readers with a summary of the findings.
## Objectives
To analyze the relationships between variables using Exploratory Data Analysis (EDA) by asking the following questions
- To find out which month has the highest and lowest accident rates and what the average rate is.
- To determine which day of the month has the highest and lowest accident rates and what the average rate is.
- To identify the time periods with the highest and lowest accident rates.
- To discover the top 5 provinces with the highest number of accidents.
- To uncover the top 3 roads or routes with the highest number of accidents.
- To determine the top 3 accident types with the highest occurrence.
- To determine which month has the highest number of fatalities and injuries combined.
- To identify the top 3 vehicle types causing the most accidents each month.
- To find out the top 3 accident characteristics with the highest occurrence each month.
- To discover which month has the highest number of accidents involving vehicles.
- To identify which vehicle types are most commonly involved in accidents based on their characteristics.
- To pinpoint which days of the month require extra caution in travel.
- To determine the weather conditions during which accidents most commonly occur.
- To calculate the proportions of individuals injured, deceased, and unharmed in accidents.
- To compare the cumulative impact of different accident types on fatalities.
## The scope of the data
- Data about road accidents in Thailand in 2022 was sourced from [https://datagov.mot.go.th/](https://datagov.mot.go.th/dataset/roadaccident/resource/94b10b47-7bda-4f11-b6ce-e45c447c8dcd?inner_span=True&activity_id=aa76337a-1f33-407d-9f83-da3a9debc826)
- There are 37 columns and 21032 rows in the raw data that was used.
  
| ตัวแปร (Variables) | ชนิดข้อมูล (Data Types) | คำอธิบายของข้อมูล (Definition) |
| :---         |     :---      |        :--- |
|ปีที่เกิดเหตุ| 	Interval|	ปีที่เกิดเหตุของอุบัติเหตุ (Year of incident)|
|วันที่เกิดเหตุ| 	Interval|	วันที่เกิดเหตุของอุบัติเหตุ (Date of incident)|
|เวลา|	Interval|	เวลาที่เกิดอุบัติเหตุ (Time of incident)|
|วันที่รายงาน|	Interval|	วันที่มีการรายงานอุบัติเหตุ (Reporting Date)|
|เวลาที่รายงาน| 	Interval|	เวลาที่มีการรายงานอุบัติเหตุ (Reporting Time)|
|ACC_CODE|	Nominal|	รหัสการเกิดอุบัติเหตุ (Accident code)|
|หน่วยงาน|	Nominal|	หน่วยงานที่เป็นผู้ดูแลเส้นทางที่เกิดอุบัติเหตุ (The agency that is in charge of the accident route)|
|รหัสสายทาง|	Nominal|	รหัสเส้นทางที่เกิดอุบัติเหตุ (The route code where the accident occurred.)|
|สายทาง	ก.ม.| 	Ratio|	กิโลเมตรที่เกิดอุบัติเหตุ (The kilometer at which the accident occurred.)|
|จังหวัด| 	Nominal|	จังหวัดที่เกิดอุบัติเหตุ (The province where the accident occurred.)|
|รถคันที่ 1| 	Nominal|	รถที่ทำให้เกิดอุบัติเหตุ (Vehicle that caused an accident.)|
|บริเวณที่เกิดเหตุ/ลักษณะทาง|	Nominal|	ลักษณะของเส้นทางที่เกิดเหตุ (The nature of the accident route)|
|มูลเหตุสันนิษฐาน|	Nominal|	ข้อสันนิษฐานที่ทำให้เกิดอุบัติเหตุ (The presumed causes leading to the accident.)|
|ลักษณะการเกิดอุบัติเหตุ| 	Nominal|	ลักษณะการเกิดอุบัติเหตุ (The characteristics of the accident occurrence.)|
|สภาพอากาศ| 	Nominal|	สภาพอากาศขณะตอนเกิดเหตุ (The weather conditions at the time of the accident.)|
|LATITUDE| 	Ratio|	พิกัดละติจูดบริเวณที่เกิดเหตุ (The latitude coordinates of the accident location.)|
|LONGITUDE|	Ratio|	พิกัดลองติจูดบริเวณที่เกิดเหตุ (The latitude coordinates of the accident location.)|
|จำนวนรถที่เกิดเหตุ (รวมคันที่ 1)| 	Nominal|	รวมจำนวนรถที่เกิดอุบัติเหตุ (รวมคันที่ทำให้เกิดอุบัติเหตุด้วย) (The number of vehicles involved in the accident, including the first vehicle that causing an accident.)|
|จำนวนรถที่เกิดเหตุทั้งหมด (รวมคนเดินเท้า)|	Nominal|	รวมจำนวนรถที่เกิดอุบัติเหตุ (รวมคนเดินเท้าด้วย) (The number of vehicles involved in the accident, including the pedestrian.)|
|รถจักรยานยนต์| 	Nominal|	จำนวนรถจักรยานยนต์ที่เกิดเหตุ (The number of motorcycles involved in the accident)|
|รถสามล้อเครื่อง| 	Nominal|	จำนวนรถสามล้อเครื่องที่เกิดเหตุ (The number of three-wheeled motor vehicles involved in the accident)|
|รถยนต์นั่งส่วนบุคคล/รถยนต์นั่งสาธารณะ| Nominal|	จำนวนรถยนต์นั่งส่วนบุคคล/รถยนต์นั่งสาธารณะที่เกิดเหตุ (The number of passenger cars/public transport vehicles involved in the accident.)|
|รถตู้|	Nominal|	จำนวนรถตู้ที่เกิดเหตุ (The number of vans involved in the accident.)|
|รถปิคอัพโดยสาร|	Nominal|	จำนวนรถปิคอัพโดยสารที่เกิดเหตุ (The number of passenger pickup trucks involved in the accident.)|
|รถโดยสารมากกว่า 4 ล้อ|	Nominal|	จำนวนรถโดยสารมากกว่า 4 ล้อที่เกิดเหตุ (The number of vehicles with more than 4 wheels involved in the accident.)|
|รถปิคอัพบรรทุก 4 ล้อ|	Nominal|	จำนวนรถปิคอัพบรรทุก 4 ล้อที่เกิดเหตุ (The number of 4-wheeled pickup trucks involved in the accident.)|
|รถบรรทุก 6 ล้อ|	Nominal|	จำนวนรถบรรทุก 6 ล้อที่เกิดเหตุ (The number of 6-wheeled trucks involved in the accident.)|
|รถบรรทุกมากกว่า 6 ล้อ ไม่เกิน 10 ล้อ|	Nominal|	จำนวนรถรถบรรทุกมากกว่า 6 ล้อ ไม่เกิน 10 ล้อที่เกิดเหตุ (The number of trucks with more than 6 wheels and up to 10 wheels involved in the accident.)|
|รถบรรทุกมากกว่า 10 ล้อ (รถพ่วง)|	Nominal|	จำนวนรถบรรทุกมากกว่า 10 ล้อ (รถพ่วง) ที่เกิดเหตุ (The number of trucks with more than 10 wheels (trailers) involved in the accident.)|
|รถอีแต๋น|	Nominal|	จำนวนรถอีแต๋นที่เกิดเหตุ (The number of agricultural vehicles involved in the accident.)|
|อื่นๆ|	Nominal|	จำนวนรถประเภทอื่นๆที่เกิดเหตุ (The number of vehicles of other types involved in the accident.)|
|คนเดินเท้า|	Nominal|	จำนวนคนเดินเท้าที่เกิดอุบัติเหตุ (The number of pedestrians involved in the accident.)|
|จำนวนผู้เสียชีวิต|	Nominal|	จำนวนผู้เสียชีวิตในอุบัติเหตุ (The number of fatalities in the accident.)|
|จำนวนผู้บาดเจ็บสาหัส|	Nominal|	จำนวนผู้บาดเจ็บสาหัสในอุบัติเหตุ (The number of seriously injured individuals in the accident.)|
|จำนวนผู้บาดเจ็บเล็กน้อย|	Nominal|	จำนวนผู้บาดเจ็บเล็กน้อยในอุบัติเหตุ (The number of slightly injured individuals in the accident.)|
|รวมจำนวนผู้บาดเจ็บ|	Nominal|	รวมจำนวนผู้บาดเจ็บทั้งหมด (The total number of injured individuals in the accident.)|

## Methodology of this project
1. Begin by performing data understanding and cleaning
  - ex. Handle missing values ​​by deleting or adding appropriate values.
    
<p align="center">
  <img width="650" height="456" src="https://github.com/Boat2356/EDA_ThaiRoadAccident2022/assets/140761543/dd632844-8224-4bd2-baab-a372798ed5d1">
</p>

2. When we have the information ready we must analyze it to find in-depth information
  - ex. Relationships of variables, appearing patterns, and calculation of statistics such as frequency, average, etc.

<p align="center">
  <img width="1491" height="400" src="https://github.com/Boat2356/EDA_ThaiRoadAccident2022/assets/140761543/5271d42d-43c0-4200-94bb-113cabd91d46">
</p>
    
3. When we finish analyzing the data, it is important to make your data easy for others to understand. Data Visualization is to creation of various graphs or charts to make it easier for us to understand in-depth information. You should choose a graph that is appropriate for the data set being analyzed.
  - ex. To determine the distribution of accident characteristics, such as rollovers, rear-end collisions, and others, a bar graph is the most appropriate choice. This is because bar graphs effectively visualize the frequency of distinct values (categories) within a qualitative dataset.

<p align="center">
  <img width="650" height="456" src="https://github.com/Boat2356/EDA_ThaiRoadAccident2022/assets/140761543/2264b87d-aa1a-4493-af24-6e206f5f5c77">
</p>

## Conclusion
Based on the analysis of the relationships between various variables using Exploratory Data Analysis (EDA) and asking different questions, the following summary can be drawn
### Which month has the highest and lowest accident rates, and what are the average rates?
- April is the month with the highest frequency of accidents, followed by January and December, with frequencies of 1993, 1897, and 1536, respectively.
- June has the lowest frequency of accidents, with a frequency of 1183.
- The average frequency of accidents each month is 1403.83.
### Which day of the month experiences the highest and lowest accident rates, and what are the average rates?
- The 1st day of every month has the highest accident frequency, followed by the 2nd and 13th days, with frequencies of 733, 658, and 620, respectively.
- The 6th day of every month has the lowest accident frequency, with a frequency of 404.
- The average frequency of accidents each day of the month is 543.42.
### What are the time periods associated with the highest and lowest accident rates?
- 3 PM has the highest accident frequency, with a frequency of 974, while 3 AM has the lowest accident frequency, with a frequency of 482.
### What are the top 5 provinces with the highest accident rates?
- The top 5 provinces with the highest accident frequency are Bangkok, Chonburi, Nakhon Ratchasima, Chiang Mai, and Suphan Buri, with frequencies of 1332, 1056, 762, 639, and 494, respectively.
### What are the top 3 roads or routes with the highest accident rates?
- The top 3 roads or routes with the highest accident frequency are 1. Straight roads with no slope, 2. Wide curved roads with no slope, and 3. Wide curved roads with a slope, with frequencies of 13503, 1974, and 805, respectively.
### What are the top 3 accident characteristics with the highest occurrence?
- The top 3 accident characteristics with the highest frequency are 1. Overturning/falling on straight roads, 2. Rear-end collisions, and 3. Overturning/falling on curved roads, with frequencies of 7804, 5205, and 2170, respectively.
### Which month has the highest combined number of fatalities and injuries?
- April has the highest number of fatalities from accidents, with a total of 277 deaths.
- April also has the highest number of injuries from accidents, with a total of 1705 injuries.
### What are the top 3 vehicle types causing the most accidents each month?
- In summary, accidents mainly involve personal vehicles/public transport vehicles and pickup trucks. Rear-end collisions occur mostly with personal vehicles/public transport vehicles while overturning/falling on straight roads is most common with pickup trucks.
### What are the top 3 accident types with the highest occurrence each month?
- The top 3 accident types with the highest frequency in each month are 1. Overturning/falling on straight roads, 2. Rear-end collisions, and 3. Overturning/falling on curved roads.
### Which month records the highest number of accidents involving vehicles?
- April has the highest number of accidents involving vehicles, including both the first vehicle and pedestrians.
### Which vehicle types are most commonly involved in accidents based on their characteristics?
- In summary, accidents mainly involve personal vehicles/public transport vehicles and pickup trucks. Rear-end collisions occur mostly with personal vehicles/public transport vehicles, while overturning/falling on straight roads is most common with pickup trucks.
### Which days of the month require extra caution in travel?
- January 1-4, April 10-18, and December 29-31 have the highest number of accidents, indicating caution during these periods.
### What are the common weather conditions during accidents?
- Accidents mostly occur in clear weather conditions, followed by rainy conditions and fog/smoke/dust.
### What are the proportions of injuries, fatalities, and non-injuries/non-fatalities in accidents?
- The majority of accidents resulted in no fatalities, accounting for 44.9%, followed by no injuries at 27.1%. There were injuries in 22.6% of cases, and the least common scenario involved fatalities at 5.06%.
### How do different accident types contribute to the total fatalities?
- Accidents are mostly caused by injuries rather than fatalities. For example, speeding violations result in more injuries than fatalities.

## Recommendation
- Data Timeliness and Relevance: The raw data used is from the year 2565 B.E. (2022 A.D.) only. Therefore, it's crucial to be cautious about how this data reflects the current situation. Consider updating the data to include more recent years to ensure its relevance and applicability to present-day scenarios.
- Data Coverage and External Factors: The raw data might not cover all relevant factors that could impact the analysis. Consider including additional variables or factors such as traffic laws, road conditions, economic conditions, and driving behaviors. These factors can significantly influence accident rates and patterns.
- Data Accuracy and Completeness: Before conducting any analysis, it's essential to verify the accuracy and completeness of the data. Check the data sources, ensure there are no missing or erroneous entries, and validate the data against other trusted sources if possible.
