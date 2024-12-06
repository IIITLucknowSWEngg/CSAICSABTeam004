#   C4 Diagrams

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


