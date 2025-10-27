# Team 4 Mist 4610 Group Project 1

## Team Name: 
15058 Group 4 

## Team Members:

1. Aadi Nag [@aadinag-uga]((https://github.com/aadinag-uga))
2. Sam Greenspan [@SamGreenspan1](https://github.com/SamGreenspan1)
3. Chase Lessing [@chase-aquaz18](https://github.com/chase-aquaz18)
4. Sam Kooran[@samuel4610](https://github.com/samuel4610)
5. Nicholas Wilson[@wilsonnj1](https://github.com/wilsonnj1)

## Scenario Description:

We are creating a realistic database to store information for MARTA in order to maximize efficiency and provide analytics that support business decisions. The central entity in the model is the trip entity, which represents each of the trips run by MARTA. The trip entity is the core service that links the physical entities of trains, depots, and stations to the riders entity which represents the people that actually use the service. We want to model relationships like how each train is a certain type, how stations are staffed by employees, and how each trip can have many stops. As well as the customer side where riders purchase different types of passes and are linked to specific trips.


## Data Model

Explanation of data model: 

Our model is based on the structure of the MARTA system and its typical operations. The Depot entity represents the different depots where the trains are stored and maintained, including information about the depot's location and capacity. Each depot is home to many trains, represented by the one to many relationship we have placed between the depot and train entities.

The train entity represents a specific train. This entity includes information about specific depotID of the depot it is associated with and the trainTypeID which represents the type of train it is. Each train has to represent one of the different types of trains, represented by a one to many relationship with the entity trainType. This entity includes the passenger capacity and manufacturer of each train. Since each train goes on multiple trips and each trip has one train, there is a one to many relationship placed between the train and the trip entity. 

The trip entity represents the departure time, arrival time, and the date for each trip, as well as linking each trip to a specific train by including a specific trainID. Since each trip has multiple stops, there is a one to many relationship between the trip entity and the Stops entity. The Stops entity details the arrival and departure times for each specific trip (represented by trip_tripID) while also linking each stop to a specific station through its stationID. Since a station has multiple stops, we have linked the Stops entity to the station entity using a one to many relationship. The station entity represents the station name, location, and operating hours. 

Each station has a full staff of employees, all with different roles and levels of seniority. Since each station has many employees but each employee can only work for one station, this relationship is conveyed through a one to many relationship linking the station entity to the Employees entity. The Employees entity represents each employee's role, the date they were hired, as well as their wage and the stationID of the station they are linked to. Out of the employees, one has to manage or supervise the others. To represent the hierarchy within the employees, we have made a recursive one to many relationship solely with the Employees entity. 

Each trip includes many riders and many riders can be on a singular trip. This is represented by a many to many relationship with the trip entity and riders entity, all leading to the trip_has_riders entity. This entity includes the tripID of the specified trip, the riderID of the rider of the train, the station where the trip started, and the station where the trip ended.

The riders entity includes identifying information about each rider including their name, phone number, date of birth, and email. Since each rider can make many transactions but each transaction is linked to a single rider, we have added a one to many relationship with the riders entity and the transaction entity. This entity includes the date of the transaction, the time it took place, the dollar amount of the transaction, as well as the riderID of the rider that completed the transaction and the passTypeID of the type of pass that was used in the transaction. Since one pass type can be sold in many different transactions, we have linked the transaction entity with the passType entity with a one to many relationship. This entity includes the duration that the pass is valid, the type of pass, and the amount of money on the pass.



<img width="811" height="722" alt="Screenshot 2025-10-16 at 5 30 57 PM" src="https://github.com/user-attachments/assets/e0fd8979-640e-4888-abbd-77e578331977" />


## Data Dictionary:





## Queries:

1. What is the revenue that comes in from each pass type? - Simple
   
<img width="1062" height="807" alt="image" src="https://github.com/user-attachments/assets/ce56dd9b-9c1c-45f6-8eca-a82ba58669d1" />

Query 1 allows managers to see which pass types received the most revenue. This is helpful for managers to identify things like which passes are the most popular, which passes need a price increase/decrease, which passes would benefit from promotions and deals, and which passes need to be stocked up more often.

2. What are the names of riders, along with the dates and amounts of their transactions that are over $50? - Simple

<img width="886" height="682" alt="image" src="https://github.com/user-attachments/assets/3cbef6fb-3604-4ead-a469-2e1305e2cda6" />


Query 2 is helpful for managers to identify high-value clients, such as clients purchasing passes in bulk. With this information, managers know things like who to incentivize or reward with deals or special promotions, especially if the purchases start to slow down from a repeat customer. It could also serve to identify suspicious activity if an unusually high purchase is made.

3. List the busiest boarding stations. - Simple




Query 3 is helpful for managers to identify which stations are the most busy. This information can help managers know how many staff and other resources need to be put towards each station to maximize efficiency and their use of resources. 

4. List the service frequency as the total number of trips per day. - Simple
 


Query 4 allows the manager to see the total number of trips made per day. This information can help the manager identify how many trips should be made on an average day. A manager can look at an above-average day and try to find out what caused the increase, or look at a below-average day to find out what caused the drop in trips. It could also help identify specific days of the week or holidays where more or less staffing is necessary.

5. List the frequent travelers (riders with more than 2 trips) - Complex
   


Query 5 allows the manager to see which travelers are marked as "frequent travelers". This information can help managers decide which customers to promote certain deals to as well as how their trip frequency is affected by certain changes made by the management. 

6. Which stations have an above average number of trips? - Complex



Query 6 allows the manager to see which stations have more than the average number of trips. Since the number of trips affects the amount of maintenance and staffing required, this information allows the manager to identify which stations could potentially need more staffing or even which ones have too many resources being put towards them.

7. Which managers supervise employees whose average wage per hour is higher than the overall system average? - Complex



Query 7 allows the managers to see which managers supervise employees who are paid higher per hour than the average. This could provide crucial information about why employee turnover is the way it is. It could also lead them to look further into the reasoning behind why they are being paid more than average and if it is worth the cost or losing them money. 

8. Identify depots that have more than 30 trains assigned to them - Complex



Query 8 helps managers to identify which depots have more than 30 trains assigned to them. This information allows managers to know which depots to pay greater attention to, as complications or shutdowns could have a much bigger impact at one of these depots than at a smaller one.

9. Find the top 5 most profitable pass types based on total transaction amounts, including average spend per rider - Complex



Query 9 allows managers to identify which are the most profitable pass types. This information could help managers identify which pass types they want to be pushed at the point of sale, as well as which ones they want to advertise the most. This information could also serve to help identify which passes would benefit from discounts and which could profit more with a raise in price.

10. Identify the top 3 trains with the highest average passenger load per trip - Complex



Query 10 identifies the top 3 trains that, on average, carry the most passengers per trip, showing their train IDs, types, capacities, total riders, total trips, and average passengers per trip. By finding which trains consistently carry the most passengers per trip, management can see which routes or train types are most popular. These are trains that are operating near or at full capacity.

## Database information:

Name of the database: ns_15058_4

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: 
CALL TP_Q1();
