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

## Database Information

Database Name: ns_71152_3

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL Group3_Q1();
