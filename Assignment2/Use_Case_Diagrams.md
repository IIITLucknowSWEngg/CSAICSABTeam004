# Use Case Diagrams

## 1. Viewer Usecase Diagram

![System Context Diagram](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/viewer_usecase.png>)

```
@startuml
' Use Case Diagram for Viewer (User) of Amazon Prime Video Clone Project

actor "Viewer" as viewer

package "Amazon Prime Video Clone (User)" {
    usecase "Browse Videos" as UC_Browse
    usecase "Search Videos" as UC_Search
    usecase "Watch Video" as UC_Watch
    usecase "Rate/Review Video" as UC_Review
    usecase "Manage Account" as UC_Account
    usecase "View Watch History" as UC_History
    usecase "Subscribe to Plan" as UC_Subscribe
    usecase "Control Playback" as UC_Control
}

' Viewer interactions
viewer --> UC_Browse
viewer --> UC_Search
viewer --> UC_Watch
viewer --> UC_Review
viewer --> UC_Account
viewer --> UC_History
viewer --> UC_Subscribe
viewer --> UC_Control

@enduml
```

## 2. Admin Usecase Diagram
![System Context Diagram](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/admin_usecase.png>)

```
@startuml
' Use Case Diagram for Admin of Amazon Prime Video Clone Project

actor "Admin" as admin

package "Amazon Prime Video Clone (Admin)" {
    usecase "Manage Videos" as UC_Manage_Videos
    usecase "Manage Users" as UC_Manage_Users
    usecase "Manage Subscriptions" as UC_Manage_Subscriptions
    usecase "View Analytics" as UC_Analytics
    usecase "Manage Payments" as UC_Manage_Payments
}

' Admin interactions
admin --> UC_Manage_Videos
admin --> UC_Manage_Users
admin --> UC_Manage_Subscriptions
admin --> UC_Analytics
admin --> UC_Manage_Payments

@enduml
```


