# ITM_Business-Analytics 
Techniques, applications, and practices for analyzing the data generated from diverse source to gain business value.   

# Project-Team6 🚁
This is a team project for __selecting the optimal location and route for air-taxi in Seoul.__     

Team members and Roles   
* Seokjun Kang : 
* Suho Lee : Build a data analysis process and Modeling
* Junseok Jeon : 
* Jihwan Hwang :    


## 1. Topic description
+ The first goal of this project is to recommend ideal locations for air taxi stations upon the introduction of such a service, aiming to identify the most optimal stops.

+ Then, the second goal is to devise an efficient routing plan between these chosen locations, providing paths that minimize travel distance for passengers.     


## 2. Problem definition   

+ As urban populations soar and the demand for efficient transportation intensifies, the current infrastructure struggles to keep pace, leading to exacerbated traffic congestion. The challenge is to innovate beyond the saturated capacity of roads and traditional public transit systems. Air taxis emerge as a prospective solution to these problems, offering an alternative mode of transportation that utilizes the underused airspace above cities.
   
+ The primary challenge is to identify strategic locations for air taxi stations that harmonize with urban layouts, optimize accessibility, and ensure maximum coverage with minimal disruption to existing city regulations. The second challenge involves developing an effective network to connect these stations, providing passengers with direct and efficient travel routes.


## 3. Purpose of the analysis   

### 1) Purpose
+ __Location Identification__: The first objective is to identify and recommend ideal locations for air taxi stations within urban areas. This involves analyzing and selecting the optimal spots for the air taxi service, taking into account social factors such as population density and the number of businesses. The focus is on ensuring these stations are easily accessible and provide extensive coverage throughout the city.   
  
+ __Routing Plan Development__: The second goal is to develop an efficient routing plan between these identified stations. This plan aims to outline the most effective paths that minimize travel distance and time for passengers, enhancing the overall efficiency of the air taxi service.   

### 2) Expected outcomes
+ __Optimal Station Locations__: This project will provide a comprehensive list of optimal locations for air taxi stations that are in harmony with the city's social and structural characteristics. Carefully selected based on important social factors such as population density and business concentration, these locations will offer extensive coverage and easy accessibility throughout the city, while minimizing the impact on the urban environment and complying with local regulations. This is expected to significantly enhance the efficiency and accessibility of the air taxi service.   

+ __Efficient Travel Routes__: A detailed routing plan that connects these stations. This plan should facilitate quick, direct, and efficient travel for passengers, significantly reducing the travel time compared to current transportation options.      

### 3) Constraints   
+ Flight, 용산만 제외   


## 4. Main Dataset
+ *OD dataset*
국가교통DB - 수도권 주수단 OD 데이터(서울 통행량 데이터 활용)
+ *Seoul subway & bus*

+ *Population Density & Number of Company*


## 5. Preprocessing
### 1) DataSet
pop_density,, 등 기초 자료등 사용한 데이터 기록, 부분적으로 api사용해서 위경도 불러온거 기록 

## 6. Model

### 1) K-means Clustering

   K-means Clustering is a distance-based clustering algorithm for dividing data into K clusters.
K-means Clustering assumes that data in the same cluster have similar features and data in different clusters have opposite features. In other words, it not only considers clustering within the same cluster, but also considers the relationship with other clusters. 
K-means clustering is simple, fast, and performs well.

> It is sensitive to outliers.
K-means Clustering is sensitive to outliers. In particular, if an outlier is selected as the centroid, it can lead to strange clustering results, so apply the model after preprocessing using <b>StandardScaler</b>.

   ![image](https://github.com/phrabit/ITM_Business-Analytics/assets/70180003/f63a883c-cce4-422a-8272-0f8c4582b997)



## 7. Our Project Flow

### 1) Feedback Reflected Clustering
   + In progress, using three features(Income level, # of companies, population density), we did clustering.
     However, it is meaningless since just ranking those features might be more efficient. Thus, we found knee points for # of companies, population density and transportation_total. Sum all of those top instances, then we proceed to do k-means clustering

     ![image](https://github.com/phrabit/ITM_Business-Analytics/assets/70180003/163a2dd4-be5d-451f-98a0-7c8cc25d55ca)


### 2) Select a specific 'Dong' for each Cluster
   +

### 3) Evaluate Transportation Access for Each Candidate ‘Dong'
   Public transportation stops within the representative candidate "dong" selected by clusters are set as candidate sites for Air taxi location, and then the priority of Air taxi location of the candidate sites is finally derived by considering the connection with other transportation methods.

1. Integration of Seoul public transportation (bus, subway) stop location information
- Collect data on bus stops in Seoul
- Collect subway station data in Seoul
- Merge bus stop and subway station data
- Finally, use the respective latitude and longitude coordinate data and administrative building information of the area (using Google Map API, Kakao API)


2. Calculate the number of other stops within 300 meters of each public transportation stop

- Why 300m?
Because the plane distance cannot exceed 300m when setting up a transfer center. Therefore, the maximum possible transfer distance between public transportation and air taxi is set to 300m. (According to the Road Traffic Administration Rules)

3. Prioritize Air taxi stops for representative candidate  "dong" in each cluster
- Data of 6 candidate "dong", one per cluster
- Data on the number of other stops within 300 meters of each public transportation stop
- Merge the two datasets.

> Candidate "dong" selection criteria
> 1) The number of subway stations within a 300m radius of each stop location is prioritized.
> 2) If the number of subway stations is the same, the number of bus stops within a 300m radius is the final prioritization.

4. Visualize the results
![image](https://github.com/phrabit/ITM_Business-Analytics/assets/70180003/e6a7bcef-ea14-421b-95a0-65ccd981c353)


### 4) Finding the optimal route among stations
   (1) Set the constraints(P-73, noise issue)  
   (2) Cost all paths according to each constraint.  - H3 (Hexagonal hierarchical geospatial indexing system)  
   (3) Find the path where cost between the two stations is minimized.(Dijkstra Algorithm)  
   ![readmeroute](https://github.com/phrabit/ITM_Business-Analytics/assets/97167373/ce0f7ad1-76cf-440c-908f-fe218b8af637)




## 8. Conclusion
 +  This project has successfully pinpointed six prime locations for air taxi stations, strategically situated near major transit points to facilitate easy access and connectivity. By leveraging a hexagonal zoning approach in Seoul and employing Dijkstra's algorithm for economical pathfinding, we've optimized air taxi routes for maximum efficiency. This initiative is poised to significantly bolster the integration with existing public transportation networks, alleviate road traffic congestion, and play a pivotal role in establishing a robust air taxi system in Seoul, with far-reaching economic benefits.
