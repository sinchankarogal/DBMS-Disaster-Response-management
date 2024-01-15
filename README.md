# DBMS-Disaster-Response-management

# E-Commerce-Database-management-project

  As a part of our course, I made this project for Database Management Systems (DBMS). This project contains theoretical as well as implementation in SQL.
  
### Contents
  •	Project Description
  
  •	Basic structure
  
    o	Functional requirements
    
    o	Entity Relation (ER) diagram and constraints
    
    o	Relational database schema
    
  •	Implementation
  
    o	Creating tables
    
    o	Inserting data
    
# Pre-requisite
  •	MySQL
  
### Project Description
  The disaster management database is used to manage information related to natural disasters and other crises. It includes data on affected areas and individuals, available resources and their locations, response teams, tasks, communications, evacuations, shelters, donations, injuries, damages, and relief efforts. The database provides quick access and sharing of critical information to aid in response efforts. It helps disaster management personnel track and manage donations and relief efforts and provide real-time updates on the status of evacuations and shelters. The entities and relationships involved in the process are modeled, and the database schema is designed for efficient retrieval and real-time updates. This database is an essential tool for managing the complex and critical process of responding to natural disasters and other emergencies.

### Relational Database Schema - e-commerce -ER diagram

![alt text](https://github.com/vivekuw/E-Commerce-Database-management-project/blob/23a0b08070f5fe22a055910cafc06d86dc3befb6/E%20commerce%20ER%20Diagram.jpg)

### ER diagram 

![alt text](https://github.com/vivekuw/E-Commerce-Database-management-project/blob/a83d9c48c82ffd18dee02c13f42e87b7069faf67/ECommerce.jpg)

### Create Schema(database) in MySQL
```sql
  create schema e_commerce;
```
### Create Tables

  Customer Table
 
 ```sql
    create table e_commerce.customer (
      customer_id int primary key,
      FirstName varchar(50),
      MiddleName varchar(50),
      LastName varchar(50),
      Email varchar(100),
      DateOfBirth date,
      phone INT(10),
      age int null
    );

 ```
  EMERGENCY_EVENT Table
  
  ```sql
 CREATE TABLE EMERGENCY_EVENT (
    EMG_ID INT PRIMARY KEY,
    DISASTER_TYPE VARCHAR(255),
    START_DATE VARCHAR(255)
);

```
   AFFECTED_AREA Table
  
  ```sql
    CREATE TABLE AFFECTED_AREA (
    AREA_ID INT PRIMARY KEY,
    POPULATION INT,
    LOCATION VARCHAR(255),
    DAMAGE_EXTENT VARCHAR(255),
    EMG_ID INT,
    FOREIGN KEY (EMG_ID) REFERENCES EMERGENCY_EVENT(EMG_ID)
);

```
AFFECTED_INDIVIDUAL Table
  
  ```sql
    CREATE TABLE AFFECTED_INDIVIDUAL (
    INDIVIDUAL_ID INT PRIMARY KEY,
    NAME VARCHAR(255),
    INJURY_TYPE VARCHAR(255),
    SEVERITY VARCHAR(255),
    AREA_ID INT,
    FOREIGN KEY (AREA_ID) REFERENCES AFFECTED_AREA(AREA_ID)
);

```
 TASK Table
  
  ```sql
  CREATE TABLE TASK (
    TASK_ID INT PRIMARY KEY,
    TASK_NAME VARCHAR(255)
);

```
EVENT_RESPONSE Table
  
```sql
  CREATE TABLE EVENT_RESPONSE (
    EMG_ID INT,
    TASK_ID INT,
    FOREIGN KEY (TASK_ID) REFERENCES TASK(TASK_ID),
    FOREIGN KEY (EMG_ID) REFERENCES EMERGENCY_EVENT(EMG_ID)
);


```
TEAM Table
  
  ```sql
   CREATE TABLE TEAM (
    TEAM_ID INT PRIMARY KEY,
    TEAM_NAME VARCHAR(255),
    TEAM_LEADER VARCHAR(255),
    EQUIPMENT VARCHAR(255),
    PERSONNEL INT,
    TASK_ID INT,
    FOREIGN KEY (TASK_ID) REFERENCES TASK(TASK_ID)
);

```
  EVACUATION Table
  
```sql
   
CREATE TABLE EVACUATION (
    EVA_ID INT PRIMARY KEY,
    TRANSPORT VARCHAR(255),
    LOCATION VARCHAR(255),
    DESTINATION VARCHAR(255),
    TEAM_ID INT,
    AREA_ID INT,
    FOREIGN KEY (AREA_ID) REFERENCES AFFECTED_AREA(AREA_ID),
    FOREIGN KEY (TEAM_ID) REFERENCES TEAM(TEAM_ID)
);

```

 RESOURCES Table

```sql
    
CREATE TABLE RESOURCES (
    RES_ID INT PRIMARY KEY,
    QUANTITY INT,
    TYPE VARCHAR(255),
    TEAM_ID INT,
    FOREIGN KEY (TEAM_ID) REFERENCES TEAM(TEAM_ID)
);

```

  DONATION Table

  ```sql
    CREATE TABLE DONATION (
    DONATION_ID INT PRIMARY KEY,
    NAME VARCHAR(255),
    TYPE VARCHAR(255),
    AMOUNT INT,
    AREA_ID INT,
    FOREIGN KEY (AREA_ID) REFERENCES AFFECTED_AREA(AREA_ID)
);

```

### Insert the data

 ```sql
  INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (101, 'Earthquake', '1998-04-14');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (102, 'Structural fire', '2002-11-22');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (103, 'Public health emergency', '2011-03-11');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (104, 'Chemical spill', '2005-08-29');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (105, 'Transportation accident', '2016-11-07');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (106, 'Wildfire', '2007-04-16');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (107, 'Structural failure', '2019-05-03');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (108, 'Oil spill in ocean', '2003-02-01');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (109, 'Animal disease outbreak', '2012-10-29');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (110, 'Hate crime', '2018-01-13');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (111, 'Airplane hijack', '2006-05-26');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (112, 'Gas leak', '2010-01-12');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (113, 'Utility failure', '2001-09-11');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (114, 'Flood', '2017-09-20');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (115, 'Terrorist attack', '2009-09-29');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (116, 'Tsunami', '1999-11-04');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (117, 'Drought', '2019-09-01');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE) 
VALUES (118, 'Large scale power outages', '2014-04-16');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE)
VALUES (119, 'Landslides', '1995-01-17');
INSERT INTO EMERGENCY_EVENT (EMG_ID, DISASTER_TYPE, START_DATE)
VALUES (120, 'Ebola', '2013-04-15');

INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (1, 1000, 'Downtown', 'Severe', 101);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (2, 500, 'Residential neighborhood', 'Moderate', 102);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (3, 200, 'Office building', 'Minor', 104);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (4, 5000, 'Coastal town', 'Severe', 116);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (5, 10000, 'Metropolis', 'Moderate', 115);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (6, 150, 'Local park', 'Minor', 105);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (7, 100, 'Shopping mall', 'Moderate', 110);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (8, 50, 'Sacred groves', 'Minor', 106);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (9, 300, 'Local Farm', 'Severe', 109);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (10, 2000, 'Suburban area', 'Minor', 118);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (11, 750, 'Office building', 'Moderate', 113);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (12, 100, 'Warlock’s village', 'Minor', 120);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (13, 50, 'Good town Apartment', 'Minor', 107);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (14, 1000, 'Elder Ville', 'Severe', 119);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (15, 500, 'Small town', 'Moderate', 106);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (16, 100, 'Old wood square', 'Minor', 118);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (17, 500, 'Oar’s rest', 'Moderate', 103);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (18, 5000, 'Rural area', 'Severe', 117);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (19, 250, 'Aurora bay', 'Minor', 114);
INSERT INTO AFFECTED_AREA (AREA_ID, POPULATION, LOCATION, DAMAGE_EXTENT, EMG_ID)
VALUES (20, 100, 'Residential area', 'Moderate', 112);



INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (201, 'John Smith', 'Broken leg', 'Moderate', 1);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (202, 'Jane Doe', 'Smoke inhalation', 'Minor', 8);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (203, 'Bob Johnson', 'Head injury', 'Severe', 1);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (204, 'Sarah Lee', 'Cuts and bruises', 'Minor', 13);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (205, 'David Chen', 'Smoke inhalation', 'Moderate', 2);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (206, 'Avery Rodriguez', 'Burns', 'Severe', 2);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (207, 'Maggie Kim', 'Sprained ankle', 'Minor', 7);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (208, 'Adam Lee', 'Smoke inhalation', 'Moderate', 20);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (209, 'Karen Williams', 'Broken arm', 'Moderate', 1);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (210, 'Mike Davis', 'Cuts and bruises', 'Minor', 5);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (211, 'Julie Baker', 'Smoke inhalation', 'Moderate', 3);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (212, 'Chris Lee', 'Burns', 'Severe', 3);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (213, 'Emily Kim', 'Broken leg', 'Moderate', 6);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (214, 'Kevin Park', 'Smoke inhalation', 'Minor', 20);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (215, 'Linda Chen', 'Head injury', 'Severe', 6);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (216, 'Nate Rodriguez', 'Cuts and bruises', 'Minor', 6);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (217, 'Olivia Johnson', 'Gun shot wounds', 'Moderate', 5);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (218, 'Ethan Brown', 'High fever', 'Severe', 17);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (219, 'Anna Smith', 'Anemia', 'severe', 18);
INSERT INTO AFFECTED_INDIVIDUAL (Individual_id, Name, Injury_type, Severity, Area_id) 
VALUES (220, 'Sam Davis', 'Hypothermia', 'Moderate', 4);

INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (601, 'Rescue');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (602, 'Medical response');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (603, 'Search and rescue');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (604, 'Fire suppression');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (605, 'Law enforcement');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (606, 'Test and reconstruct');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (607, 'Management');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (608, 'Wildlife management');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (609, 'Conveyance');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (610, 'Communication');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (611, 'Food supply');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (612, 'Tools management');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (613, 'Decontamination');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (614, 'Power supply management');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (615, 'Press releases');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (616, 'Delivery');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (617, 'Equipment management');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (618, 'Security surveillance');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (619, 'Air rescue');
INSERT INTO TASK (TASK_ID, TASK_NAME) VALUES (620, 'Environmental monitoring');

INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (101, 603);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (101, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (119, 601);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (119, 607);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (104, 613);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (102, 604);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (103, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (103, 615);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (105, 609);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (105, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (106, 604);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (106, 620);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (107, 603);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (107, 617);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (108, 615);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (109, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (109, 608);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (110, 605);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (110, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (111, 619);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (111, 615);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (112, 612);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (112, 618);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (113, 606);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (113, 612);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (120, 615);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (120, 602);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (115, 618);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (115, 605);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (115, 610);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (116, 601);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (116, 611);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (117, 611);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (117, 616);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (118, 614);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (114, 601);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (114, 611);
INSERT INTO EVENT_RESPONSE (EMG_ID, TASK_ID) VALUES (114, 602);


INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (301, 'Rescue Squad Alpha', 'Javon Lee', 'Rescue gear', 10, 601);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (302, 'Medical Response Team', 'Antonio Ward', 'Medical supplies', 8, 602);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (303, 'Search and Rescue Team', 'Esteban Ashley', 'Safety tool pack', 12, 603);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (304, 'Firefighters', 'Khloe Hardin', 'Fire truck', 15, 604);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (305, 'Police Unit', 'Mathias Fuller', 'Patrol cars', 20, 605);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID)
VALUES (306, 'Engineering Team', 'Martin Martinez', 'Engineering Tools', 7, 606);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (307, 'Volunteers', 'Alexa Horton', 'N/A', 30, 607);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID)
VALUES (308, 'Animal Control Team', 'Nick Dennis', 'Animal cages', 5, 608);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (309, 'Transportation Team', 'Jacob Villa', 'Vehicles', 10, 609);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (310, 'Communication Team', 'Maddox Kline', 'Communication Gadgets', 6, 610);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (311, 'Food and Supplies Team', 'Lucy Walter', 'Ration kits', 12, 611);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (312, 'Equipment Maintenance Team', 'Antony Fox', 'Spare parts', 8, 612);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (313, 'Hazmat Team', 'Leanna Ortega', 'Decontamination equipment', 10, 613);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (314, 'Power and Utilities Team', 'Miya Mcknight', 'Generators', 15, 614);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (315, 'Public Information Team', 'Kayden Alvarado', 'Media equipment', 5, 615);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (316, 'Logistics Team', 'Makenzie Jarvis', 'Inventory management system', 8, 616);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (317, 'Construction Team', 'Maximo Lozano', 'Construction tools', 12, 617);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (318, 'security Team', 'Mylie Dickerson', 'Security alarms', 15, 618);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (319, 'Air Support Team', 'Aaliyah Arellano', 'Helicopters', 5, 619);
INSERT INTO TEAM (TEAM_ID, TEAM_NAME, TEAM_LEADER, EQUIPMENT, PERSONNEL, TASK_ID) 
VALUES (320, 'Environmental Team', 'Jeffrey Case', 'Environmental monitoring equipment', 7, 620);

INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (1, 'Boat', '123 Main St.', '456 Elm St.', 301, 19);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (2, 'Ambulance', '789 Oak Ave.', '234 Maple St.', 302, 12);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (3, 'Helicopter', '567 Pine St.', '890 Cedar St.', 303, 1);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (4, 'Fire truck', '345 Walnut St.', '678 Birch St.', 304, 8);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (5, 'Ambulance', '901 Cherry St.', '234 Apple St.', 305, 7);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (6, 'Fire truck', '567 Orange St.', '890 Grape St.', 304, 2);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (7, 'Helicopter', '345 Lemon St.', '678 Lime St', 307, 14);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (8, 'Ambulance', '123 Peach St.', '456 Plum St.', 308, 9);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (9, 'Ambulance', '789 Banana St', '234 Pear St.', 309, 6);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (10, 'Military vans', '567 Mango St.', '890 Pineapple St.', 310, 5);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (11, 'Boat', '345 Kiwi St.', '678 Watermelon St.', 311, 4);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (12, 'Ambulance', '123 Cantaloupe St.', '456 Honeydew St.', 312, 20);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (13, 'Hazmat vehicles', '789 Papaya St.', '234 Cherry St.', 313, 3);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (14, 'Fire truck', '567 Grapefruit St.', '890 Tangerine St.', 314, 16);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID) 
VALUES (15, 'Ambulance', '345 Pear St.', '678 Orange St.', 315, 17);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID)
VALUES (16, 'Bus', '123 Mango St.', '456 Pineapple St.', 316, 18);
INSERT INTO EVACUATION (EVA_ID, TRANSPORT, LOCATION, DESTINATION, TEAM_ID, AREA_ID)
VALUES (17, 'Bus', '789 Strawberry St.', '234 Blueberry St.', 317, 13);

INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (401, 50, 'Water', 304);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (402, 75, 'Food', 311);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (403, 100, 'Medical supplies', 302);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (404, 25, 'Blankets', 301);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (405, 10, 'Flashlights', 303);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (406, 20, 'Tents', 320);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (407, 30, 'Batteries', 313);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (408, 5, 'First aid kits', 302);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (409, 40, 'Water', 304);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (410, 60, 'Blankets', 311);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (411, 15, 'Flashlight', 318);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (412, 80, 'Food', 301);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (413, 90, 'Medical supplies', 308);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (414, 35, 'Tents', 305);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (415, 70, 'Batteries', 318);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (416, 45, 'Water', 307);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (417, 55, 'Food', 320);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (418, 10, 'Construction tools', 317);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (419, 25, 'Vehicles', 309);
INSERT INTO RESOURCES (RES_ID, QUANTITY, TYPE, TEAM_ID) VALUES (420, 30, 'Security alarms', 318);

INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (501, 'John Smith', 'Cash', 5000, 1);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (502, 'Jane Doe', 'Supplies', 1500, 20);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (503, 'Bob Johnson', 'Cash', 2500, 19);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (504, 'Samantha Lee', 'Supplies', 4500, 17);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (505, 'Chris Williams', 'Cash', 1000, 9);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (506, 'Melanie Davis', 'Supplies', 500, 2);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (507, 'Tom Jackson', 'Cash', 2000, 4);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (508, 'Laura Brown', 'Supplies', 3000, 19);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (509, 'Alex Nguyen', 'Cash', 7500, 14);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (510, 'Rachel Hernandez', 'Supplies', 900, 1);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (511, 'Robert Lee', 'Cash', 600, 8);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (512, 'Emily Johnson', 'Supplies', 1500, 12);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (513, 'William Kim', 'Cash', 1000, 5);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (514, 'Jennifer Brown', 'Supplies', 500, 6);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (515, 'Michael Davis', 'Cash', 2000, 15);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (516, 'Sarah Kim', 'Supplies', 1000, 17);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (517, 'Timothy Wilson', 'Cash', 2600, 19);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (518, 'Katie Jones', 'Supplies', 4600, 7);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (519, 'Juan Rodriguez', 'Cash', 3200, 12);
INSERT INTO DONATION (DONATION_ID, NAME, TYPE, AMOUNT, AREA_ID) VALUES (520, 'Megan Smith', 'Supplies', 1000, 9);


 ```


QUERIES

1. Find the total number of individuals affected by each emergency event, and list the events in descending order of the total number of affected individuals

```sql
SELECT e.Emg_id, COUNT(i.Individual_id) AS NumAffected
FROM EMERGENCY_EVENT e
JOIN AFFECTED_AREA a ON e.Emg_id = a.Emg_id
JOIN AFFECTED_INDIVIDUAL i ON a.Area_id = i.Area_id
GROUP BY e.Emg_id
ORDER BY NumAffected DESC;

```

2.Find the total number of individuals affected by events that were
responded to by  the Police Unit.

```sql

SELECT E1.Disaster_TYPE,COUNT(A1.NAME)
FROM AFFECTED_INDIVIDUAL A1,AFFECTED_AREA A2,EMERGENCY_EVENT E1,EVENT_RESPONSE E2,TEAM T
WHERE A1.AREA_ID=A2.AREA_ID AND A2.EMG_ID=E1.EMG_ID AND E1.EMG_ID=E2.EMG_ID AND
E2.TASK_ID=T.TASK_ID AND T.TEAM_NAME='Police Unit' 
GROUP BY E1.Disaster_TYPE

```

3. Retrieve the number of individuals affected in each severity category for each emergency event.
   
```sql

SELECT EMERGENCY_EVENT.Disaster_Type, AFFECTED_INDIVIDUAL.severity, COUNT(*) 
FROM AFFECTED_INDIVIDUAL 
JOIN AFFECTED_AREA ON AFFECTED_INDIVIDUAL.area_id = AFFECTED_AREA.area_id JOIN EMERGENCY_EVENT ON AFFECTED_AREA.Emg_id = EMERGENCY_EVENT.Emg_id
GROUP BY EMERGENCY_EVENT.disaster_Type, AFFECTED_INDIVIDUAL.severity;

```

4. Give the number of events that each team has responded to.

```sql
SELECT Team_name, COUNT(*) AS total_events
FROM TEAM
INNER JOIN EVENT_RESPONSE ON TEAM.Task_id = EVENT_RESPONSE.Task_id
GROUP BY Team_name;
```


6. List the emergency event and affected individuals in Downtown

```sql
SELECT Disaster_TYPE,NAME
FROM EMERGENCY_EVENT E, AFFECTED_AREA A1,AFFECTED_INDIVIDUAL A2
WHERE E.EMG_ID=A1.EMG_ID AND A1.AREA_ID=A2.AREA_ID AND A1.LOCATION='Downtown'
JOIN AFFECTED_AREA a ON e.Emg_id = a.Emg_id
JOIN AFFECTED_INDIVIDUAL i ON a.Area_id = i.Area_id

```


7. Display the name of area with highest affected
population with location and damage extent

```sql

SELECT LOCATION,DAMAGE_EXTENT,POPULATION
FROM AFFECTED_AREA
WHERE POPULATION=(SELECT MAX(POPULATION)
                                        FROM AFFECTED_AREA)
```
                                          
8. Find the number of emergency events that each team has responded to, and list the teams in descending order of the number of events they have responded to.

```sql

SELECT t.Team_id, t.Team_name, count( e.Emg_id)
FROM TEAM t,EVENT_RESPONSE e
where t.task_id=e.task_id
GROUP BY t.Team_id, t.Team_name
ORDER BY count( e.Emg_id) DESC

```


8. Retrieve the task names and the corresponding team names and leader  involved in responding to emergencies with the largest affected population area.

```sql
select tr.task_name,t.team_name,t.team_leader
from task tr,team t
where t.task_id=tr.task_id and tr.task_id in(select task_id
                    from event_response
                     where emg_id in(select emg_id
                                    from affected_area
                                    where population=(select max(population)
                                                       from affected_area)))
group by tr.task_name,t.team_name,t.team_leader

```


9. What is the count of injury type for individuals affected
by each emergency event?

 ```sql
select e.disaster_type,count(a2.injury_type)
from emergency_event e
join affected_area a1 on e.emg_id=a1.emg_id
join affected_individual a2 on a1.area_id=a2.area_id
group by e.disaster_type

```

10. Retrieve all the emergency events that occurred after 2005

```sql
SELECT EMG_ID,disaster_TYPE,START_DATE
FROM EMERGENCY_EVENT 
WHERE start_date > '2005';

```

11. Give the names of all individuals who have been affected by an event in area id 1

```sql
SELECT ai.Name 
FROM AFFECTED_INDIVIDUAL ai 
INNER JOIN AFFECTED_AREA aa ON ai.Area_id = aa.Area_id 
WHERE aa.Area_id = 1;

```

12. Retrieve the donation amounts and types received by emergency events involved in responding to emergencies

```sql
select d.area_id,sum(d.amount),ee.disaster_type
from donation d,affected_area aa,emergency_event ee
where d.area_id=aa.area_id and aa.emg_id=ee.emg_id
group by d.area_id,ee.disaster_type
order by sum(d.amount) desc

```

13. Give the number of individuals affected by each severity level.

```sql

SELECT Injury_type, Severity, COUNT(*) AS total_individuals
FROM AFFECTED_INDIVIDUAL
GROUP BY Injury_type, Severity;

```


14.	Display the locations of affected area where individuals are severly injured in any emergency event

```sql
SELECT LOCATION
FROM AFFECTED_AREA A1,AFFECTED_INDIVIDUAL A2
WHERE A1.AREA_ID=A2.AREA_ID AND A2.SEVERITY='Severe'
```

15. Retrieve the names of all individuals affected by emergencies that required the "'Medical response'" task.

```sql
select ai.name,ai.area_id
from affected_individual ai
where ai.area_id in(select aa.area_id
                    from affected_area aa,event_response er,task tr
                    where aa.emg_id=er.emg_id and er.task_id=tr.task_id 
                    and tr.task_name='Medical response')

```

16.List the team names and their tasks who use bus  for evacuation

```sql
SELECT T1.TEAM_NAME,T2.TASK_name,e1.area_id
FROM TEAM T1,TASK T2,EVACUATION E1
WHERE T1.TASK_ID=T2.TASK_ID AND E1.TEAM_ID=T1.TEAM_ID 
AND E1.TRANSPORT='Bus' 

```

17.Display the quantity of supplies with their name utilized during earthquake

```sql
SELECT R.TYPE,R.QUANTITY
FROM RESOURCES R,TEAM T1,EVENT_RESPONSE E1,EMERGENCY_EVENT E2
WHERE R.TEAM_ID=T1.TEAM_ID AND T1.TASK_ID=E1.TASK_ID AND E1.EMG_ID=E2.EMG_ID 
AND E2.disaster_TYPE='Earthquake'
```

18.Display the  no of teams involved during each emergency event
```sql
SELECT E2.DISASTER_TYPE,COUNT(T1.TEAM_ID)
FROM EMERGENCY_EVENT E2,EVENT_RESPONSE E1,TEAM T1
WHERE E2.EMG_ID=E1.EMG_ID AND E1.TASK_ID=T1.TASK_ID
GROUP BY E2.DISASTER_TYPE
```

19. Give the count of all emergency events.
```sql
SELECT COUNT(*) 
AS total_emg_events 
FROM EMERGENCY_EVENT;
```

20.Retrieve the total quantity of resources used by teams involved in responding to emergencies of a certain disaster type.
```sql
select sum(quantity)
from resources
where team_id in(select team_id
from team
where task_id in(select task_id
from event_response
where emg_id in(select emg_id
                from emergency_event
                where  disaster_type='Earthquake')))

```


21. Display the name of area with number of affected individuals reported for each event

```sql
SELECT A1.LOCATION,E.DISASTER_TYPE,COUNT(A2.INDIVIDUAL_ID)
FROM AFFECTED_AREA A1,AFFECTED_INDIVIDUAL A2,EMERGENCY_EVENT E
WHERE A1.AREA_ID=A2.AREA_ID AND A1.EMG_ID=E.EMG_ID
GROUP BY A1.LOCATION,E.DISASTER_TYPE
```

22.Retrieve the number of teams involved in event 105.

```sql
SELECT COUNT(DISTINCT Task_id) 
FROM EVENT_RESPONSE
WHERE emg_id = 105;
```

23.Calculate the total number of individuals affected by events that  occurred in areas with a damage extent of severe and were responded to by teams with a task id of 602.
```sql
SELECT COUNT(*) AS TotalAffectedIndividuals
FROM AFFECTED_INDIVIDUAL ai
JOIN AFFECTED_AREA aa ON ai.AREA_ID = aa.AREA_ID
JOIN EVENT_RESPONSE er ON aa.EMG_ID = er.EMG_ID AND er.Task_ID = 602
WHERE aa.DAMAGE_EXTENT = 'Severe';
```

24. Retrieve the names of all affected individuals and their severity level in areas where the population is above 500.
```sql
SELECT ai.NAME, ai.SEVERITY
FROM AFFECTED_INDIVIDUAL ai 
WHERE ai.AREA_ID IN ( SELECT aa.AREA_ID 
                      FROM AFFECTED_AREA aa 
                      WHERE aa.POPULATION > 500)

```
25. Retrieve the number of individuals affected in each injury type.
```sql
SELECT injury_type, COUNT(*)
FROM AFFECTED_INDIVIDUAL 
GROUP BY injury_type;
```

27. Retrieve the start time of the emergency with the largest affected area.
```sql
select start_date
 from emergency_event
 where emg_id in( select emg_id
 from affected_area
 where population in(select max(population)
          from affected_area))
```

27. Give the average population of areas affected by each emergency event.
```sql
SELECT Emg_id, AVG(Population) AS avg_population
FROM AFFECTED_AREA
GROUP BY Emg_id;
```

28.Retrieve the names of all affected individuals and the corresponding area name where the disaster occurred:
```sql
SELECT ai.NAME, aa.LOCATION 
FROM AFFECTED_INDIVIDUAL ai 
INNER JOIN AFFECTED_AREA aa ON ai.AREA_ID = aa.AREA_ID 
WHERE ai.AREA_ID = aa.AREA_ID; 
```

29.Retrieve the names of all teams and leader involved in the disaster response and their corresponding task name:
```sql
SELECT t.TEAM_NAME, tr.TASK_NAME ,t.team_leader
FROM TEAM t,task tr
where t.task_id=tr.task_id 
```

30. Find all tasks that are required for emergencies that occurred in locations with a population greater than 1000:
```sql
select  task_name
from task
where task_id in(select er.task_id
                 from event_response er,affected_area aa
                 where er.emg_id=aa.emg_id and aa.population>1000)
```

                
 31. Retrieve the name and severity of injury of the affected individuals for EMG_ID 105.
```sql
SELECT NAME, SEVERITY 
FROM AFFECTED_INDIVIDUAL 
WHERE AREA_ID IN ( SELECT AREA_ID
                   FROM AFFECTED_AREA 
                WHERE Emg_id = 105 );
```
               
32. Retrieve the names of the tasks required for EMG_ID 103.
```sql
SELECT TASK_NAME 
FROM TASK
WHERE TASK_ID IN ( SELECT TASK_ID
                    FROM EVENT_RESPONSE  
                    WHERE EMG_ID = 103 );

```

33.Create a view to display the total quantity of each resource used in the emergency response:

```sql
CREATE VIEW resource_summary_view AS 
SELECT r.TYPE, SUM(r.QUANTITY) AS TOTAL_QUANTITY 
FROM RESOURCE r 
GROUP BY r.TYPE;
```

34.Create a view to display the number of teams assigned to each task required for a specific emergency:

```sql
CREATE VIEW task_assignment_view AS 
SELECT tr.TASK_NAME, COUNT(t.TEAM_ID) AS NUM_TEAMS 
FROM TASK tr 
JOIN TEAM t ON tr.TASK_ID = t.TASK_ID 
JOIN EVENT_RESPONSE er ON t.TEAM_ID = er.TEAM_ID 
WHERE er.EMG_ID = 101 
GROUP BY tr.TASK_NAME;
```

35. Create a procedure that deletes all records of a given disaster type from the database.
```sql
CREATE  PROCEDURE NEW_DELETE_DISASTER_TYPE (disaster_type IN VARCHAR2) 
IS
BEGIN 
  DELETE FROM AFFECTED_AREA 
  WHERE Emg_id IN ( SELECT Emg_id FROM EMERGENCY_EVENT WHERE disaster_Type = disaster_type ); 
  DELETE FROM AFFECTED_INDIVIDUAL 
  WHERE Area_id IN ( SELECT Area_id FROM AFFECTED_AREA WHERE Emg_id IN ( SELECT Emg_id FROM EMERGENCY_EVENT WHERE Type = disaster_type ) ); 
  DELETE FROM EVENT_RESPONSE WHERE Emg_id IN ( SELECT Emg_id FROM EMERGENCY_EVENT WHERE Type = disaster_type ); 
  DELETE FROM EMERGENCY_EVENT WHERE disaster_Type = disaster_type; 
END;
/
```

37. Create a function that returns the number of individuals affected by a given emergency event.
```sql
CREATE FUNCTION GET_NUM_AFFECTED11 ( emg_id INT ) 
RETURN INT 
IS 
  num_affected INT; 
BEGIN 
  SELECT COUNT(*) INTO num_affected
  FROM AFFECTED_INDIVIDUAL 
  WHERE Area_id IN (SELECT Area_id FROM AFFECTED_AREA WHERE Emg_id = emg_id); 
  RETURN num_affected;
END;
```

























