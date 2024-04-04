@startuml

title Job Placement System - Detailed Architecture

node "Client Browser" as client {
}

node "Load Balancer" as lb {
}

node "Web Server" as webServer {
  artifact "React App" as reactApp
  component "Web Server" as webServerComp {
    component "HTTP Server" as httpServer
    component "Static Content" as staticContent
    component "Node.js App" as nodeApp {
      component "Client-Side Routing" as clientRouting
      component "REST API Proxy" as restApiProxy
      component "User Interface" as ui
      component "User Authentication" as userAuth
      component "Session Management" as sessionManagement
      component "Error Handling" as errorHandling
      database "User Session" as userSession
    }
  }
}

node "Application Server" as appServer {
  artifact "Matching Algorithm" as matchAlgorithm
  artifact "Profile Management" as profileManagement
  artifact "Drive Management" as driveManagement
  component "REST API" as appRestApi
  component "Student Actions" as studentActions
  component "Recruiter Actions" as recruiterActions
  component "College Actions" as collegeActions
  component "Admin Actions" as adminActions
  component "Database Access" as dbAccess
}

node "Database Server" as dbServer {
  database "UserDB" as userDB
  database "JobDB" as jobDB
  database "DriveDB" as driveDB
  database "ApplicationDB" as appDB
}

client --> lb : HTTP Request
lb --> webServer : Forward
webServer --> client : HTML, CSS, JavaScript
webServer --> appServer : REST API Request
appServer --> webServer : REST API Response
appServer --> dbServer : CRUD Operations

@enduml
