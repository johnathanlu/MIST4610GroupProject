# Team 3 MIST4610 71552 Group Project 

## Team Members

1. Brooks Lawson [@blaw05303](https://github.com/blaw05303)
2. Ishaan Prasad [@ishaanprasad1](https://github.com/ishaanprasad1)
3. John Paul [@johnpaul1111-hub](https://github.com/johnpaul1111-hub)
4. Johnathan Lu [@johnathanlu](https://www.github.com/johnathanlu)
5. Madison Jin [@madisonajin-bot](https://github.com/madisonajin-bot)
6. Maxwell Alton Buckingham [@mabuckingham](https://github.com/mabuckingham)

## Problem Description
Our scenario is to create the “Last-Mile” Urban Logistics (Drone Delivery) system, focusing on fleet maintenance and route optimization to ensure efficient and reliable operations. The drones are the core of the system, operating with other entities including routes, packages, maintenance logs, technicians, and charging stations. Our three main goals include ensuring drones have a clearly defined status (in-flight, charging, or under maintenance) before being assigned new packages, creating new maintinence logs every 50 drone hours, and having charging stations host one drone track the start and end times. We aim to accurately model the relationship between all these entities as well as create queries to etc etc.


## Data Model
<img width="1312" height="848" alt="Drone_Actual" src="https://github.com/user-attachments/assets/20720547-6420-4450-b303-797b1ac7eed1" />


A drone delivery system manages drones, routes, technicians, packages, maintenance logs, technicians, and charging stations.

Drones are used to deliver packages. The drone table includes information regarding model type, carrying capacity, speed, flight status, charging status, and total hours. This is important information used to see which drones are good to go to deliver the packages to the customers. Drones are charged via charging stations. The charging station table contains information about charger availability, station type, and charging status of the drone. A port can have many charging stations but a charging station can only have one port. A charging station can hold multiple drones, and a drone can visit multiple charging stations. Each instance of a drone charging is called a charging session. 

Technicians help upkeep the drones and perform regular maintenance. The technician table includes information about the technician’s name, phone, pay, and hours worked. A technician can work on many drones, and a drone requires multiple technicians to be worked on due to the many complicated parts of a drone. A maintenance log is created for every instance that a drone is worked on by a technician. The MaintenanceLog contains the maintenancelogID, technicianID, hoursAtMaintenance, maintenanceType, maintenanceDetails, maintenanceStart, and maintenanceEnd. 

A lead technician works at one port, but multiple technicians can also work at this one port. The lead technician acts as a ‘boss’ in this sense. Hence there is a one to one relationship between the technicians and ports table as well as a one to many from ports to technicians. 
 
Items are inside a package. A port can contain multiple different items, and the same item can be at multiple ports. A port inventory log is used to keep track of the quantity in stock of a particular item at a particular port. Additionally, we created a PackageItems table as the associative entity between PortInventory and PackageDetails. There are multiple PackageItems records that link to one PortInventory, so multiple PackageItems can reference the same inventory item.  

Drones deliver packages from ports via routes. A route belongs to one port but a port has many routes.  The route table has information about which unique route it is, where the route ends, and whether the route is available or not. If a route is already occupied or there is a shorter route to deliver the package to the customer, then this table will indicate this to us. A port can hold many drones, but a drone belongs to a specific port.  A drone can go on multiple routes, and each route can have multiple drones. A flightlog is created for each instance a specific drone is on a specific route.

A port can hold many packages, and each package will only ever belong to one port. Each package has a log known as “packagedetails” that keeps track of the package’s date of packaging and the delivery status.  The packagedetails reference a single address, but an address can receive multiple packages. Additionally, addresses each reference one customer, but a customer can have multiple addresses (work, divorce, etc.)  A single flightlog is created for each package. A customer can have many packages, but each package belongs to a specific customer. 

## Data Dictionary
<img width="723" height="480" alt="image" src="https://github.com/user-attachments/assets/2e743d7f-c677-476c-ac01-43c153aa5ebc" />

<img width="722" height="407" alt="image" src="https://github.com/user-attachments/assets/da29c4fd-e1e9-4ea9-9ed3-ec25469ad1f2" />

<img width="737" height="272" alt="image" src="https://github.com/user-attachments/assets/24e0799c-5cce-49b5-b28f-b2d5c159d866" />

<img width="735" height="500" alt="image" src="https://github.com/user-attachments/assets/3811915f-4691-4f3c-acb6-c43404624fb9" />

<img width="732" height="484" alt="image" src="https://github.com/user-attachments/assets/5fed6955-92bc-4201-804d-ab21f5e74b1c" />

<img width="737" height="390" alt="image" src="https://github.com/user-attachments/assets/d7d501d7-d6a5-4c96-8e22-37d4dc1ccf15" />

<img width="737" height="722" alt="image" src="https://github.com/user-attachments/assets/467f5f18-f743-49ad-a194-477f6b177b3a" />

<img width="715" height="714" alt="image" src="https://github.com/user-attachments/assets/7a9823a8-c902-4572-a100-78c312064968" />

<img width="722" height="720" alt="image" src="https://github.com/user-attachments/assets/eb177084-6e2d-4f15-af32-eeff71da1d05" />

<img width="712" height="866" alt="image" src="https://github.com/user-attachments/assets/dc3832b0-5bd8-4715-a194-0c3b874a5e8a" />

<img width="615" height="798" alt="image" src="https://github.com/user-attachments/assets/9b388cd1-f6ef-4579-abda-02450e2fe242" />

<img width="623" height="642" alt="image" src="https://github.com/user-attachments/assets/c31d9f4c-e89c-44a5-966a-f7a4c6be4778" />

<img width="613" height="512" alt="image" src="https://github.com/user-attachments/assets/cac2226b-d8d3-4ed1-9382-b049f0951c83" />

<img width="612" height="681" alt="image" src="https://github.com/user-attachments/assets/dffd5594-ddf8-4fe2-99b0-42fe3e31de22" />

## List of Queries

<img width="713" height="844" alt="image" src="https://github.com/user-attachments/assets/a8fe3b3f-c1f0-4cc3-a4e2-9b4f3cd41322" />


1.
<img width="1175" height="394" alt="image" src="https://github.com/user-attachments/assets/6e1b7cb9-43c1-4bdf-b664-baefa0d4d87a" />

Query 1 lists the drone ID, model, and flight status of all drones that never had maintenance.
This query helps managers track the newest drones they acquired, seeing how they perform without maintenance or repairs. This provides information on the longevity of each drone model, helping managers determine which models to purchase if additional drones are required.

2.
<img width="1339" height="842" alt="image" src="https://github.com/user-attachments/assets/eb269ee1-dbdc-41f0-9cf4-d51721ec8278" />

Query 2 lists the technician name and the amount of hours they worked in the second half of the month. 
This will be used by managers to determine their pay for the period as well as track employee performance. Those that work significantly more hours than others may be considered for bonuses or promotions. This can also be used to track direct labor hours on budgeting sheets.

3.
<img width="956" height="631" alt="image" src="https://github.com/user-attachments/assets/ecb8bde0-d162-41cc-8b82-d5361c0a3372" />

Query 3 lists the package ID, customer tied to the package, weight of the package, status of the package, and weight category created based on the weight.
This query helps with the labeling and shipping of the packages. Heavy packages can be labeled for the awareness of the people handling it, giving them a cautionary warning. Additionally, package weights categories can be used to determine different shipping medians (ex. plane vs truck) and be used to somewhat distribute weight evenly when placing in vehicles.

4.
<img width="1011" height="450" alt="image" src="https://github.com/user-attachments/assets/4e48846d-62a6-4f2a-826f-e676e4a97413" />

Query 4 lists the customer name, the amount of packages they have if they have more than one, and the total weight of the combined packages. 
This could be used by the packaging team to determine if it is optimal to ship a customer's packages together or separate to reduce shipping fees.

5.
<img width="1014" height="484" alt="image" src="https://github.com/user-attachments/assets/a74f85cd-09c8-49cf-a051-f1932f1bfe54" />

Query 5 lists the port name and location for ports in Athens that have drones that are actively in flight. 
This is useful to managers so that they can actively monitor flight activity within different regions. This can be easily altered to gather the same information for different cities or regions. Managers can also use this for incident response such as inclement weather that could disrupt service. 

6.
<img width="1316" height="728" alt="image" src="https://github.com/user-attachments/assets/60392a5a-0f81-47c4-9d31-3f50580b3df1" />

Query 6 lists the drone ID, model of the drone, and the amount of times they have had maintenance performed on them. 
This query can be used to help track the age and amount of hours each drone has flown for logistic purposes. Those with more maintenance are inherently older. If drones reach a certain maintenance threshold or are not functioning properly, managers can retire and replace them with new drones.

7.
<img width="1140" height="703" alt="image" src="https://github.com/user-attachments/assets/db4637e8-28dd-48e9-8ccd-6366847b4c94"/>
 
Query 7 lists the port name, specific name, and amount of stock if the port has less than 100 of the item.
This query can be used to help determine item allocation. Ports low in stock of a certain item will likely need it sooner than others, helping managers determine which ports get priority shipping for certain items. 

8.
<img width="1323" height="771" alt="image" src="https://github.com/user-attachments/assets/6b47c083-bbd3-4bc6-9f6f-f9f7c786deaf" />

Query 8 lists the droneID, flightDateTime, completionDateTIme, the number of days that a delivery took, and categorizes the deliveries as same day, next day, within 3 days, or more than three days. 
This query can be used by managers to track any flight duration irregularities. By grouping flights by duration managers can immediately see if the drone fleet is meeting its service requirements. The manager can use this over time to see if delivery speeds are improving or declining over time. 

9.
<img width="998" height="376" alt="image" src="https://github.com/user-attachments/assets/5883792c-d039-4c3a-aa1f-8f4bfd423854" />

Query 9 joins the ports and technicians table to list the port info along with the lead technicians name and salary. 
This is useful to managers so that they can monitor their salary distribution across different hubs. They can compare the location of the port and the salary to determine if the compensation provided to the lead technicians is consistent with the cost of living or with the specific responsibilities of that port. 

10.
<img width="768" height="505" alt="image" src="https://github.com/user-attachments/assets/b85fc1af-f199-4909-8c21-b67b618f799a" />

Query 10  lists the customer name, packageID, status, and weight of packages that exceed the calculated average weight of packages. 
This information helps managers identify trends in high load orders. This can help with maintenance forecasting as frequent high load flights but stress on the mechanical components of the drone fleet. Weight also affects drone range and speed which can be processed by managers to determine appropriate surcharges and service expectations for better transparency with customers. 


## Database Information

Database Name: ns_71152_3

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL Group3_Q1();
