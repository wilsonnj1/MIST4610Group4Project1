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



<img width="886" height="723" alt="image" src="https://github.com/user-attachments/assets/482edd0f-4c6d-4bd9-8720-55c879ca0581" />


## Data Dictionary:

<img width="1072" height="427" alt="image" src="https://github.com/user-attachments/assets/efd30b0c-137e-4b05-b059-05d6055e19dd" />

<img width="1057" height="752" alt="image" src="https://github.com/user-attachments/assets/6aa6457b-ca6d-44dd-b43d-7a357751f311" />

<img width="957" height="615" alt="image" src="https://github.com/user-attachments/assets/6d37f27e-c8a9-4bf5-ac84-607fe2a08bf6" />

<img width="1020" height="635" alt="image" src="https://github.com/user-attachments/assets/8c8d7a70-8d6d-446a-ba7c-ee2075f87810" />

<img width="992" height="512" alt="image" src="https://github.com/user-attachments/assets/f6bbd59e-f58c-41f5-a740-0fe501185319" />

<img width="1142" height="685" alt="image" src="https://github.com/user-attachments/assets/36f7cf7a-6a9e-41ce-97f1-41cb606aa4c4" />

<img width="1048" height="501" alt="image" src="https://github.com/user-attachments/assets/a2d66b95-f598-4615-9f7f-94498857650b" />

<img width="986" height="492" alt="image" src="https://github.com/user-attachments/assets/1a12fae1-c4bc-472f-b265-f95191d96545" />

<img width="995" height="758" alt="image" src="https://github.com/user-attachments/assets/d938af65-ae88-4fc8-9d54-6fef724d4ad6" />

<img width="882" height="538" alt="image" src="https://github.com/user-attachments/assets/fcfeac5b-26b7-4a14-b632-1d43d0045b4e" />

<img width="962" height="562" alt="image" src="https://github.com/user-attachments/assets/104dc199-e471-4c5e-8db5-b49b1a2e18a4" />


## Queries:
<img width="918" height="547" alt="image" src="https://github.com/user-attachments/assets/39713232-9933-4c18-aa94-76d96b62a36f" />

1. What is the revenue that comes in from each pass type? - Simple
   
<img width="1062" height="807" alt="image" src="https://github.com/user-attachments/assets/ce56dd9b-9c1c-45f6-8eca-a82ba58669d1" />

Query 1 allows managers to see which pass types received the most revenue. This is helpful for managers to identify things like which passes are the most popular, which passes need a price increase/decrease, which passes would benefit from promotions and deals, and which passes need to be stocked up more often.

2. What are the names of riders, along with the dates and amounts of their transactions that are over $50? - Simple

<img width="886" height="682" alt="image" src="https://github.com/user-attachments/assets/3cbef6fb-3604-4ead-a469-2e1305e2cda6" />


Query 2 is helpful for managers to identify high-value clients, such as clients purchasing passes in bulk. With this information, managers know things like who to incentivize or reward with deals or special promotions, especially if the purchases start to slow down from a repeat customer. It could also serve to identify suspicious activity if an unusually high purchase is made.

3. List the busiest boarding stations. - Simple

<img width="887" height="343" alt="image" src="https://github.com/user-attachments/assets/35b7b9c1-4ce1-448e-8c4f-8818cd57d120" />



Query 3 is helpful for managers to identify which stations are the most busy. This information can help managers know how many staff and other resources need to be put towards each station to maximize efficiency and their use of resources. 

4. List the service frequency as the total number of trips per day. - Simple
 
<img width="881" height="655" alt="image" src="https://github.com/user-attachments/assets/6c119d30-8c02-40d2-b8a6-7e32164319b4" />


Query 4 allows the manager to see the total number of trips made per day. This information can help the manager identify how many trips should be made on an average day. A manager can look at an above-average day and try to find out what caused the increase, or look at a below-average day to find out what caused the drop in trips. It could also help identify specific days of the week or holidays where more or less staffing is necessary.

5. List the frequent travelers (riders with more than 2 trips) - Complex
   
<img width="886" height="368" alt="image" src="https://github.com/user-attachments/assets/b265cd01-430b-491a-8b3f-353a5c6c4759" />


Query 5 allows the manager to see which travelers are marked as "frequent travelers". This information can help managers decide which customers to promote certain deals to as well as how their trip frequency is affected by certain changes made by the management. 

6. Which stations have an above average number of trips? - Complex

<img width="886" height="501" alt="image" src="https://github.com/user-attachments/assets/59e9b967-45eb-4afc-bfbc-80c0504770c8" />


Query 6 allows the manager to see which stations have more than the average number of trips. Since the number of trips affects the amount of maintenance and staffing required, this information allows the manager to identify which stations could potentially need more staffing or even which ones have too many resources being put towards them.

7. Which managers supervise employees whose average wage per hour is higher than the overall system average? - Complex

<img width="888" height="748" alt="image" src="https://github.com/user-attachments/assets/5869d19d-8cf1-42ad-95bb-b6ac822da298" />


Query 7 allows the managers to see which managers supervise employees who are paid higher per hour than the average. This could provide crucial information about why employee turnover is the way it is. It could also lead them to look further into the reasoning behind why they are being paid more than average and if it is worth the cost or losing them money. 

8. Identify depots that have more than 30 trains assigned to them - Complex

<img width="887" height="412" alt="image" src="https://github.com/user-attachments/assets/4968f1a9-9576-46df-abe2-19000f7a15e5" />


Query 8 helps managers to identify which depots have more than 30 trains assigned to them. This information allows managers to know which depots to pay greater attention to, as complications or shutdowns could have a much bigger impact at one of these depots than at a smaller one.

9. Find the top 5 most profitable pass types based on total transaction amounts, including average spend per rider - Complex

<img width="885" height="377" alt="image" src="https://github.com/user-attachments/assets/083e8575-03bd-46a4-8d5b-d6c9f114cc55" />


Query 9 allows managers to identify which are the most profitable pass types. This information could help managers identify which pass types they want to be pushed at the point of sale, as well as which ones they want to advertise the most. This information could also serve to help identify which passes would benefit from discounts and which could profit more with a raise in price.

10. Identify the top 3 trains with the highest average passenger load per trip - Complex

<img width="887" height="421" alt="image" src="https://github.com/user-attachments/assets/d44a5d5b-69fb-414d-b77c-181668abf361" />


Query 10 identifies the top 3 trains that, on average, carry the most passengers per trip, showing their train IDs, types, capacities, total riders, total trips, and average passengers per trip. By finding which trains consistently carry the most passengers per trip, management can see which routes or train types are most popular. These are trains that are operating near or at full capacity.

## Database information:

Name of the database: ns_F25MIST4610_15058_Group4

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: 
CALL TP_Q1();
