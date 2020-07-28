# .NET App Migration Checklist

Almost any web app can be migrated to Azure PaaS given enough time and effort. This checklist can be used to assess an App in the early stages of a migration project. It is a list of common technical scoping questions that an engineer may ask.

The checklists on this page are for a .NET Framework _rehost_ scenario:

* .NET (full) Framework (not .NET Core)
* .NET Framework 3.5 or greater
* Microsoft SQL Server version 2008 R2 or greater
* Target state is Windows App Service Plans / App Service Environments (not Cloud Services, VMSS, AKS, Containers, Linux, IIS VMs)
* Target state is Azure SQL DB or Azure SQL MI (not SQL Server VMs)

## Current state

What is currently deployed and where. What are the dependencies.

> 💡 **[Azure Migration Center]** offers resources, tools and programmes for evaluating and performing Web App Migrations. 

> 💡 Consider using an evaluation tool like the [App Service Migration Tool] or a third party tool to scan and generate a report on the current state. 

#### Web tier

1. On-prem | Another Cloud | Azure VMs?
1. What version .NET Framework?
1. Web Forms? | MVC? (What version) | Web API?
1. More than one VM node?
1. Load balancer?
1. Which Session State Provider?
1. How many VMs, cores. How much RAM per VM?
1. How many websites?
1. VMs have single role or are shared with SQL/WCF/Windows Services/Other?
1. Do App Pools have user Identity (other than LOCALSYSTEM)?

#### WCF services

1. WCF services used? 
1. Same VM (tier) as Web or separate?
1. HTTPS bindings?
1. What type auth?

#### DB tier

1. What version SQL Server?
1. How many VMs, cores. How much RAM per VM?
1. How many DBs and what size?
1. Sharded DBs? Shard master?
1. SQL Server using local Timezone or UTC?

#### Networking & Security

1. Are websites private (internal / intranet) or public?
1. DMZ?
1. WAF? Audit or Block?

#### IAM

1. ASP.NET Web Forms Auth? ASP.NET Identity Framework? | Identity Server?
1. How are users Authenticated?
1. How are users Authorized?
1. Usernames and Passwords stored in Database?
1. OAuth / OpenId compliant Auth?

#### SMTP

1. IIS SMTP?
1. SQL Sendmail?
1. Private SMTP Gateway?
1. Port 25 open for outbound?


#### Compatibility Checks

1. Any MSI installed components?
1. Any GAC'ed DLLs
1. Any binary references?
1. Any GO statements in SQL?
1. Any cross-DB joins in SQL?
1. Any .NET CLR Functions


## Target State

#### App Services

1. App Service Plan / App Service Environment?


#### Azure SQL

1. Azure SQL DB?
   1. vCore or DTU model>?
   1. Elastic Pool?
1. Azure SQL MI?


## Compatibility Tasks

1. REFACTOR: Nuget packages for all references
1. REFACTOR, REARCHITECT: Split non-packagable references into seperate de-coupled services (Crystal
   Reports, ABCPDF...)
1. REHOST / REFACTOR: Remove GO statements from SQL or use SQL MI
1. REFACTOR, REARCHITECT: Split sprocs, views and queries that rely on cross-db joins into multiple
   Db calls at the Data Layer. Or use SQL MI.
1. REHOST: Turn on simple-auth with AAD for authentication
1. REHOST: Replace SMTP service with SendGrid. Refactor send mail calls if not configurable with AppSettings.
1. REHOST / REFACTOR: Refactor DateTime helper to support UTC time, Refactor sprocs to take a `@now`
   parameter. Or, use SQL MI.
1. Use SQL or Redis Session State provider (is there a Cosmos DB sessio state provider)


## Cloud Adoption Framework (CAF) and Landing Zone

What CAF and Landing zone tasks need to be complete to enable a successful migration? 

### Blueprint

1. Hub & spoke Subscriptions
1. Hub & spoke network
1. Azure Security Center Standard
1. Azure Monitor
1. Application Insights

### Networking checks

1. Connectivity to on-prem services
1. HTTP Internet access inbound
1. Firewall
1. WAF
1. DDOS

### Networking tasks

1. Express Route private pairing or Site-to-site VPN
1. App Services VPN Integration
1. Express Route public pairing
1. Azure Firewall or NVA
1. Azure App Gateway + WAF or Azure Front door
1. DDoS standard

### Monitoring tasks

1. Azure Monitor: Perfmon - SQL and IIS style counters
1. Application Insights: Performance, Errors

### Security tasks

1. Azure Security Center Standard

## Apps Platform

1. Identity
1. App Deployment pipeline
1. Metrics
1. Logging
1. APM
1. Hosting

## Tooling features

What features should be prioritised for App Migration and Modernisation tooling?

### Migration

1. App type, version, framework, framework version
1. How many tiers
1. How many apps in IIS, dependencies
1. Virtual directories
1. WCF endpoints and types
1. Logging configuration and sinks
1. APM SDK version and details (Application Insights, New Relic)
1. DB type
1. Average RPM
1. Core count, percent used by w3wp
1. RAM used by w3wp
1. Remote dependencies (WCF, SQL, HTTP)
1. In-proc dependencies (DLLs, GAC, Nuget)
1. MSI installed libraries / frameworks
1. DB count
1. Cross-DB joins
1. SQL: Go statements
1. SQL Use of GETDATE()
1. DateTime: use of non-UTC times (DateTime.Now, type = local)
1. SMTP traffic and service
1. ASP Auth Framework
1. Check for NTLM or AD
1. Check for passwords in SQL Table
1. DNS settings
1. Root CA, SSL certs, etc
1. Can server see Internet on 443, 80, etc
1. Default gateway
1. DNS server and settings
1. Scoring of complexity and project size (Wim)

### Modernisation

1. Percent sync vs async entry points
1. CDN used?
1. Output cache used?
1. Caching objects used?
1. Session state, Web Forms Session

## Links

[Azure Migration Center]:https://azure.microsoft.com/en-us/migration/
[App Service Migration Tool]:https://appmigration.microsoft.com/