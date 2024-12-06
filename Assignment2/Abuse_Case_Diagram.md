# Abuse Case Diagram


![Abuse Case Diagram](<https://github.com/IIITLucknowSWEngg/CSAICSBTeam004/blob/main/Assets/error_case_diagram.png>)
 
 ```

@startuml
title Error Case Diagram - Amazon Prime Video Clone

actor "Subscriber" as user
actor "Admin" as admin

' Main System Use Cases
usecase "Stream Video" as UC_Stream
usecase "Search Video" as UC_Search
usecase "Subscribe to Plan" as UC_Subscribe
usecase "Upload Content" as UC_Upload
usecase "Manage User Accounts" as UC_ManageUsers
usecase "Process Payment" as UC_Payment

' Error Cases for Subscriber
usecase "(Video Not Available)" as Error_VideoNotAvailable
usecase "(Content Buffering Issues)" as Error_Buffering
usecase "(Payment Failed)" as Error_PaymentFailed
usecase "(Subscription Expired)" as Error_SubscriptionExpired
usecase "(Search Error)" as Error_Search

' Error Cases for Admin
usecase "(Upload Failure)" as Error_UploadFailure
usecase "(User Management Error)" as Error_UserManagement

' Relationships for Subscriber
user --> UC_Stream : "Watch Videos"
user --> UC_Search : "Search for Content"
user --> UC_Subscribe : "Subscribe to Plan"
user --> UC_Payment : "Make Payment"

UC_Stream --> Error_VideoNotAvailable : "If content is missing"
UC_Stream --> Error_Buffering : "If network issues occur"
UC_Subscribe --> Error_SubscriptionExpired : "If subscription expires"
UC_Payment --> Error_PaymentFailed : "If payment fails"
UC_Search --> Error_Search : "If content cannot be found"

' Relationships for Admin
admin --> UC_Upload : "Upload Content"
admin --> UC_ManageUsers : "Manage User Accounts"

UC_Upload --> Error_UploadFailure : "If content upload fails"
UC_ManageUsers --> Error_UserManagement : "If user management fails"

@enduml


 ```