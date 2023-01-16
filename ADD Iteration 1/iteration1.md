# SOFE 3650 Final Project Iteration 1

## Step 1: Review Inputs
The focus of this section is to present the results of the activities that are performed in each of the steps in iteration 1 of the ADD design process. The requirements and quality attributes are refined in iteration 1, from step 2 to step 7.

| Category | Details |
| --------------| ----------------|
| Design Purpose | This application exists in a mature domain and the purpose is to produce adequately detailed design that supports the construction of the system. |
| Primary Functional Requirements | <ul><li>UC-1: Because it is a core component of the business</li> <li>UC-4: Because it is a core component of the business</li> <li>UC-5: Because of the technical issues that it associates.</li></ul> |
## Step 2: Establish Iteration Goal by Selecting Drivers
 - QA-1:Privacy
 - QA-2:Availability
 - QA-4:Accessibility
 - QA-5:Security
 - CON-1: Network Connection between user and system must be reliable.
 - CON-4: At least 100 users must be able to access the system at the same time.
 - CON-3: A database server must be used
 - CON-5: Must have a backup server for the system.
 - CRN-2: Ensure that all information is kept private. 
  ### Context Diagram for Course Management System
 ![image](https://user-images.githubusercontent.com/80362352/201563395-e2d65ee8-d958-4b3b-95de-354b9c10dd44.png)

## Step 3: Choose One or more Elements of the System to Refine 
The entire CMS is being refined as showcased in the figure above. Decomposition is the method for the refinement.

## Step 4: Choose one or more Design Concepts that Satisfy the Selected Drivers
| Design decisions and Location | Rationale |
| --------------| ----------------|
| Logically structure the client part of the system using Web Application reference architecture | Web application architecture defines the interactions between applications, middleware systems and databases to ensure multiple applications can work together. This is the best option for implementing the client server as we need a network connection between user and system(CON-1) so the application will have to be accessed through a web browser. This application also supports  user interface, business logic, data access and security(QA-5) which is needed for our application. <br> <br> Discarded alternatives: Rich internet applications(RIA): This reference architecture is oriented toward the development of applications with a rich user interface that runs inside a web browser. This option was discarded as it there was no need for a plug-in that could run the application <br> <br> Mobile applications: This reference architecture is oriented toward the development of applications that are deployed in handheld devices. This alternative was discarded because mobile devices were not considered for accessing the system as resources would be limited.|
| Logically structure the server part of the system using Service Application reference architecture | Service applications is the best fit because this part of the system does not need to be interactive and this application contains components responsible for exposing services and exchanging information |
Physically structure the application using the three-tier deployment pattern | Since the system must be accessed by user using a network connection(CON-1) and an existing database server(CON-3) must also be used, a three-tier deployment is appropriate |
Build the interface of the client application using JavaSwing | The interface shall be built using these as the team is already familiar with it and it is user friendly. |
Deploy the application using Spring Framework | Although it is complex, spring provides industry standard security(QA-5), availability(QA-2) and can integrate with other web UI.
## Step 5: Instantiate Architectural Elements, Allocate Responsibilities, and Define Interfaces
| Design decisions and Location | Rationale |
| --------------| ----------------|
|Another backup server | In case of a failure in the server or parts of it another server should be made as a backup so that availability requirements are always met(CON-5).|
Put business logic into server side | This will help to ensure that user information is kept private.(CRN-2).

## Step 6: Sketch Views and Record Design Decsions
### Web application diagram
![image](https://user-images.githubusercontent.com/80362352/201565071-ded8f051-a701-4d3b-80e5-81c4d9612dc4.png)
| Component Name | Responsibility |
| ------------ | ----------- |
|Presentation Layer | This moudle represents the client facing application and controlls use cases and user interaction |
| User Interface | Contains UI elements and responsible for presenting infromation and reciving user's interaction |
| Business Layer | This modules is respobsible for performing business logic operations |
| Endpoints | Responsible for making the business layer operation acessible to the user interface |
| Buisness Workflows | Responsible for coordinating buisness processes |
| Buisness Logic | Responsible for retrieving and processing application data and applying business rules to this data. |
| Buisness Entities | Represent the entities from the business domain and associated business logic |
| Data Layer | Represent components responsible for data persistence and communication with time servers|
| Database Deployment | Responsible for the storage and access to data accross user systems and accesspoints|
| Service Agents | Responsible for abstract communication mechanisms use to transfer data to external services |
| Crosscutting Layer | Modules that are applied to the whole system |
| Secuirty | Crosscutting functionacility that handles authorization and authentication |
| Communication | Crosscutting functionacility that handles communication accross layers | 
| Operation Management | Crosscutting functionacility such as logging, validation and exception management |

### Deployment Model
![image](https://user-images.githubusercontent.com/80362352/201565476-55101f59-5d9a-4394-b8df-26ce67a8d034.png)

## Step 7: Perform Analysis of Current Design and Review Iteration Goal and Design Objective
| Not Addressed | Partially Addressed | Completley Addressed | Design Decisions made During this Iteration |
| --------------| --------------------| --------------------| ---------------------------------------------|
| CON-4 | | | No decision was made as demand for 100 users is not present and demand response was discussed. |
| | QA-4 | | Reliable user accessibility is important to the system. The device on which the user accesses the system affect their experience so we made decisions affecting the access the system on certain devices|
| | CRN-2 | | To ensure user privacy we decided to implement server side business logic to keep user private information safe from the client side. |
| |  | CON-5 | To address CON-5 we decided to implement a backup server to handle full or partial failures on the main server.  |
| | CON-1 | | We made a decision to implement a three tier deployment to ensure a reliable user-system connection.  |
| | QA-5 | | To ensure user security we decided to implement business logic on the server side giving a greater security to the application. |
| | QA-2 | | To address availability. We implemented a three tier deployment framework and a backup server to handle failures. |
| | CON-3 | | We decided to implement a server side database to satisfy CON-3 |
| | QA-1 | | We implemented server side business logic to keep user private information from being accessible to unauthorized users on the client side.  |
| UC-4 | | | No decision made to address this use case. |
| | | UC-5 | We decided to implement a backup server to enable this use case. |
| | UC-1 | | To allow users to view course information we decided to implement the JavaSwing Framework to build a pleasing user interface. |