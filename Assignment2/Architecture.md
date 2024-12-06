#   C4 Diagrams
# 1. System Context Diagram

![System Context Diagram](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/system_ctxt_dia.png>)

```
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

LAYOUT_TOP_DOWN()
title System Context Diagram - Amazon Prime Video Clone

Person(user, "Subscriber", "Streams content, browses library, manages subscriptions")
Person(admin, "Admin", "Manages platform, monitors content")
Person(advertiser, "Advertiser", "Manages ad campaigns for freemium users")
Person(contentProvider, "Content Provider", "Uploads and licenses content")

System(primeVideoClone, "Prime Video Clone Platform", "On-demand video streaming and subscription platform")

System_Ext(storage, "Cloud Storage", "Stores video and metadata securely")
System_Ext(cdn, "CDN", "Optimized delivery of media content")
System_Ext(payment, "Payment Gateway", "Manages subscription billing")
System_Ext(email, "Email Service", "Handles notifications and alerts")
System_Ext(analytics, "Analytics", "Tracks user behavior and engagement")
System_Ext(adNetwork, "Ad Network", "Programmatic ad management")
System_Ext(transcoder, "Transcoding Service", "Optimizes video formats for streaming")
System_Ext(search, "Search Engine", "Indexes and retrieves catalog data")
System_Ext(ml, "ML Service", "AI-driven personalized recommendations")
System_Ext(moderation, "Content Moderation", "Ensures content compliance with policies")

Rel(user, primeVideoClone, "Streams content", "HTTPS")
Rel(contentProvider, primeVideoClone, "Uploads/licenses content", "HTTPS")
Rel(admin, primeVideoClone, "Administers platform", "HTTPS")
Rel(advertiser, primeVideoClone, "Creates ad campaigns", "HTTPS")

Rel(primeVideoClone, storage, "Stores media", "API")
Rel(primeVideoClone, transcoder, "Processes video formats", "API")
Rel(primeVideoClone, cdn, "Delivers media content", "HTTPS")
Rel(primeVideoClone, ml, "Provides recommendations", "gRPC")
Rel(primeVideoClone, search, "Indexes content", "API")
Rel(primeVideoClone, analytics, "Monitors user activity", "API")
Rel(primeVideoClone, adNetwork, "Integrates ads", "API")
Rel(primeVideoClone, email, "Sends notifications", "SMTP")
Rel(primeVideoClone, moderation, "Ensures content compliance", "API")
Rel(primeVideoClone, payment, "Processes payments", "API")
@enduml
```

# 2. Container Diagram
![Customer Features component](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/container_dia.png>)

```
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

skinparam {
    RectangleBackgroundColor #C08080
    RectangleBorderColor #A06060
    RectangleFontColor #FFFFFF
    ArrowColor #A06060
    ArrowThickness 2
    ArrowStyle dashed
}

LAYOUT_TOP_DOWN()
title Container Diagram - Amazon Prime Video Clone

Person(subscriber, "Subscriber", "Watches videos, manages subscriptions, and browses content")
Person(contentPartner, "Content Partner", "Uploads and licenses media content")
Person(advertiser, "Advertiser", "Runs ad campaigns and tracks performance metrics")

System_Boundary(primeVideoClone, "Prime Video Clone") {
    Container(webApp, "Web Application", "React", "Web-based user interface")
    Container(mobileApp, "Mobile Application", "Swift/Kotlin", "Mobile user interface")
    Container(apiGateway, "API Gateway", "Express.js", "Entry point for backend services")
    
    Container(videoService, "Video Service", "Node.js", "Handles video uploads, storage, and streaming")
    Container(userService, "User Service", "Django", "Manages user authentication and profiles")
    Container(subscriptionService, "Subscription Service", "Ruby on Rails", "Handles subscriptions and payments")
    Container(adService, "Ad Service", "Go", "Integrates and manages advertisements")
    Container(searchService, "Search Service", "Elasticsearch", "Enables content search and discovery")
    Container(recommendationService, "Recommendation Service", "TensorFlow", "Provides personalized video suggestions")
    Container(analyticsService, "Analytics Service", "Python", "Tracks user engagement and generates insights")
    Container(notificationService, "Notification Service", "Node.js", "Sends email and push notifications")
    Container(transcodingService, "Transcoding Service", "FFmpeg", "Converts video formats for adaptive streaming")
    Container(contentModerationService, "Content Moderation Service", "Python", "Ensures uploaded content meets platform standards")

    ContainerDb(videoDB, "Video DB", "MongoDB", "Stores metadata for videos")
    ContainerDb(userDB, "User DB", "PostgreSQL", "Stores user profiles and preferences")
    ContainerDb(subscriptionDB, "Subscription DB", "PostgreSQL", "Manages subscription data")
    ContainerDb(analyticsDB, "Analytics DB", "BigQuery", "Stores and processes engagement data")
    ContainerDb(cache, "Cache", "Redis", "Speeds up data retrieval")
    ContainerDb(messageQueue, "Message Queue", "RabbitMQ", "Processes asynchronous events")
}

System_Ext(cloudStorage, "Cloud Storage", "Stores video files securely")
System_Ext(contentDeliveryNetwork, "CDN", "Optimizes video delivery")
System_Ext(paymentGateway, "Payment Gateway", "Processes payment transactions")

Rel(subscriber, webApp, "Uses", "HTTPS")
Rel(subscriber, mobileApp, "Uses", "HTTPS")
Rel(contentPartner, webApp, "Uploads content and manages licenses", "HTTPS")
Rel(advertiser, webApp, "Manages ad campaigns", "HTTPS")

Rel(webApp, apiGateway, "Sends requests to backend", "HTTPS")
Rel(mobileApp, apiGateway, "Sends requests to backend", "HTTPS")

Rel(apiGateway, videoService, "Handles video operations", "gRPC")
Rel(apiGateway, userService, "Manages user operations", "gRPC")
Rel(apiGateway, subscriptionService, "Handles subscription operations", "gRPC")
Rel(apiGateway, searchService, "Searches content catalog", "gRPC")
Rel(apiGateway, adService, "Retrieves ads for users", "gRPC")

Rel(videoService, cloudStorage, "Stores video files", "API")
Rel(videoService, contentDeliveryNetwork, "Delivers video to users", "HTTPS")
Rel(videoService, transcodingService, "Processes video formats", "API")

Rel(subscriptionService, paymentGateway, "Processes payments", "API")

Rel(videoService, videoDB, "Stores video metadata", "MongoDB")
Rel(userService, userDB, "Stores user profiles", "PostgreSQL")
Rel(subscriptionService, subscriptionDB, "Manages subscription data", "PostgreSQL")
Rel(analyticsService, analyticsDB, "Stores engagement metrics", "BigQuery")
Rel(notificationService, messageQueue, "Processes notification events", "AMQP")
@enduml
```
# 3. Component Diagram 

### i) Customer Features
![Customer Features component](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/viewer%20%20component%20diagram.png>)
```
@startuml
' Component Diagram for Viewer Features of an Amazon Prime Video Clone

skinparam componentStyle rectangle

' External User
actor "Viewer" as viewer

' Components
component "UI Layer" as UI
component "Video Streaming Service" as VSS
component "Search Service" as SS
component "Recommendation Service" as RS
component "Account Management" as AM
component "Payment Service" as PS
component "Playback Control" as PC

' Relationships
viewer --> UI : "Interacts"
UI --> SS : "Searches for content"
UI --> RS : "Receives recommendations"
UI --> AM : "Manages account details"
UI --> PS : "Makes payments"
UI --> VSS : "Streams video content"
UI --> PC : "Controls playback (Play, Pause, etc.)"
VSS --> PC : "Handles playback"

' Database for Video Content and Account Details
database "Video Content DB" as VDB
database "Account DB" as ADB

' Connections to databases
VSS --> VDB : "Fetches video content"
AM --> ADB : "Accesses user details"
RS --> VDB : "Fetches recommended videos"

@enduml
```
### ii) Admin Features
![alt text](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/admin%20component%20diagram.png>)

```
@startuml
' Component Diagram for Admin Features of an Amazon Prime Video Clone

skinparam componentStyle rectangle

' External Actor
actor "Admin" as admin

' Components
component "Admin Dashboard" as AD
component "Content Management Service" as CMS
component "User Management Service" as UMS
component "Subscription Management Service" as SMS
component "Analytics Service" as AS
component "Payment Gateway" as PG

' Databases
database "Content DB" as CDB
database "User DB" as UDB
database "Payment DB" as PDB

' Relationships
admin --> AD : "Accesses"
AD --> CMS : "Manages content"
AD --> UMS : "Manages users"
AD --> SMS : "Manages subscriptions"
AD --> AS : "Views analytics"
AD --> PG : "Manages payment settings"

' Content Management and Databases
CMS --> CDB : "Adds/Edits/Removes content"
UMS --> UDB : "Accesses user details"
SMS --> PDB : "Handles subscription details"
PG --> PDB : "Processes payments"
AS --> CDB : "Fetches content data"
AS --> UDB : "Fetches user data"

@enduml

```

# 4. DeployMent Diagram 

 
![ DeployMent Diagram](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/deplyoment%20diagram1.png>)

```
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Deployment.puml

LAYOUT_WITH_LEGEND()
title Deployment Diagram - Amazon Video Clone

Deployment_Node(client, "Client Tier", "User Devices") {
    Deployment_Node(browser, "Web Browser") {
        Container(web, "Web App", "React", "Single Page Application for content streaming and account management")
    }
    Deployment_Node(mobile, "Mobile Device") {
        Container(app, "Mobile App", "React Native", "Supports offline downloads and adaptive streaming")
    }
}

Deployment_Node(api, "API Tier", "AWS ECS/Kubernetes") {
    Deployment_Node(api_cluster, "API Cluster", "Load Balanced") {
        Container(api_gateway, "API Gateway", "Express.js", "Handles all incoming requests with validation and rate limiting")
        Container(service, "Backend Service", "Node.js", "Manages user accounts, subscriptions, and video catalog")
        Container(auth_service, "Authentication Service", "OAuth2/OpenID", "Handles login, token management, and secure sessions")
    }
    Deployment_Node(streaming, "Streaming Service", "AWS Media Services") {
        Container(stream_server, "Streaming Server", "HLS/DASH", "Provides adaptive bitrate streaming for video playback")
    }
}

Deployment_Node(data, "Data Tier", "AWS RDS/S3/DynamoDB") {
    Deployment_Node(databases, "Database Cluster") {
        ContainerDb(user_db, "User Database", "Amazon RDS", "Stores user information and subscriptions")
        ContainerDb(metadata_db, "Content Metadata", "DynamoDB", "Stores video metadata and catalog details")
    }
}

Deployment_Node(storage, "Storage Tier", "Global") {
    Deployment_Node(object_storage, "Object Storage") {
        Container(video_store, "Video Storage", "Amazon S3", "Stores video files and static assets like thumbnails")
    }
    Deployment_Node(cdn_nodes, "CDN Nodes") {
        Container(cdn, "CDN", "AWS CloudFront", "Delivers video content globally with low latency")
    }
}

Deployment_Node(monitoring, "Monitoring and Security") {
    Container(logging, "Logging", "AWS CloudWatch", "Captures request and error logs for analysis")
    Container(metrics, "Metrics", "Prometheus/Grafana", "Monitors performance and usage trends")
    Container(security, "Web Application Firewall (WAF)", "AWS WAF", "Blocks malicious traffic and protects APIs")
}

Rel(web, api_gateway, "Sends requests", "HTTPS")
Rel(app, api_gateway, "Sends requests", "HTTPS")
Rel(api_gateway, auth_service, "Authenticates users", "OAuth2")
Rel(api_gateway, service, "Routes to", "REST")
Rel(service, user_db, "Reads/Writes", "SQL")
Rel(service, metadata_db, "Reads/Writes", "DynamoDB")
Rel(stream_server, video_store, "Streams video files", "S3 API")
Rel(video_store, cdn, "Serves to", "HTTPS")
Rel(web, cdn, "Streams video", "HTTPS")
Rel(app, cdn, "Streams video", "HTTPS")

' Error Handling Relationships
Rel(api_gateway, logging, "Logs errors and invalid requests", "HTTPS")
Rel(api_gateway, security, "Protects against request floods and large headers", "WAF Rules")
Rel(service, logging, "Logs backend errors and bad requests", "HTTPS")
@enduml
```



