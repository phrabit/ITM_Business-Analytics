![image](https://github.com/phrabit/ITM_Business-Analytics/assets/97167373/ab3be61c-8b7e-49d1-a79b-458e6d55ec8a)# ITM_Business-Analytics 
Techniques, applications, and practices for analyzing the data generated from diverse source to gain business value.   

# Project-Team6 🚁
This is a team project for __selecting the optimal location and route for air-taxi in Seoul.__     

Team members and Roles   
* 강석준: 
* 이수호: 
* 전준석: 
* 황지환:    


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
사진+ 간략한 설명예정
+ *OD dataset*

+ *Seoul subway & bus*

+ *Population Density & Number of Company*


## 5. Preprocessing
### 1) DataSet
pop_density,, 등 기초 자료등 사용한 데이터 기록, 부분적으로 api사용해서 위경도 불러온거 기록 

## 6. Model

### 1) K-means Clustering
   + 설명, 하는 역할 

### 2) Agglomerative hierarchical clustering
   + 설명 및 안쓰는이유


## 7. Our Project Flow

### 1) Feedback Reflected Clustering
   +  How to Clustering is....

### 2) Select a specific 'Dong' for each Cluster
   +

### 3) Evaluate Transportation Access for Each Candidate ‘Dong'
   + Sue..Help

### 4) Finding the optimal route among stations
   + (1) Set the constraints(P-73, noise issue)
   + (2) Cost all paths according to each constraint.  - H3 (Hexagonal hierarchical geospatial indexing system)
   + (3) Find the path where cost between the two stations is minimized.(Dijkstra Algorithm)



## 8. Conclusion
 +  This project has successfully pinpointed six prime locations for air taxi stations, strategically situated near major transit points to facilitate easy access and connectivity. By leveraging a hexagonal zoning approach in Seoul and employing Dijkstra's algorithm for economical pathfinding, we've optimized air taxi routes for maximum efficiency. This initiative is poised to significantly bolster the integration with existing public transportation networks, alleviate road traffic congestion, and play a pivotal role in establishing a robust air taxi system in Seoul, with far-reaching economic benefits.
