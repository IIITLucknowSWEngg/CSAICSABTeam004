![dia](https://github.com/user-attachments/assets/b699309e-206f-4a70-b8e8-ea0f630b02ff)
@startuml
left to right direction
title Amazon Prime Video - Abuse Case Diagram

actor Attacker
actor FraudulentUser as "Fraudulent User"
actor BotNetwork as "Bot Network"
actor MaliciousDeveloper as "Malicious Developer"

usecase "SQL Injection" as SQLInjection
usecase "Cross-Site Scripting (XSS)" as XSS
usecase "Phishing" as Phishing
usecase "Data Breach Attempt" as DataBreach

usecase "Credential Sharing Abuse" as CredentialSharing
usecase "Account Hijacking" as AccountHijacking
usecase "Content Piracy" as ContentPiracy
usecase "Fake Reviews/Engagement" as FakeEngagement

usecase "Automated Fake Engagement" as FakeEngagementBots
usecase "Scraping Video Metadata" as ScrapingMetadata
usecase "Content Flooding" as ContentFlooding

usecase "API Exploitation" as APIExploitation
usecase "Unauthorized Content Hosting" as UnauthorizedHosting
usecase "Injection of Malicious Code" as MaliciousCode

usecase "Trust Loss" as TrustLoss
usecase "Revenue Loss" as RevenueLoss
usecase "Data Compromise" as DataCompromise

Attacker --> SQLInjection
Attacker --> XSS
Attacker --> Phishing
Attacker --> DataBreach

FraudulentUser --> CredentialSharing
FraudulentUser --> AccountHijacking
FraudulentUser --> ContentPiracy
FraudulentUser --> FakeEngagement

BotNetwork --> FakeEngagementBots
BotNetwork --> ScrapingMetadata
BotNetwork --> ContentFlooding

MaliciousDeveloper --> APIExploitation
MaliciousDeveloper --> UnauthorizedHosting
MaliciousDeveloper --> MaliciousCode

SQLInjection --> TrustLoss
XSS --> TrustLoss
DataBreach --> DataCompromise
CredentialSharing --> RevenueLoss
AccountHijacking --> TrustLoss
ContentPiracy --> RevenueLoss
FakeEngagement --> TrustLoss
FakeEngagementBots --> TrustLoss
ScrapingMetadata --> DataCompromise
APIExploitation --> DataCompromise
UnauthorizedHosting --> RevenueLoss

@enduml
