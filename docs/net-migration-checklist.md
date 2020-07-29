# .NET App Migration Checklist

Almost any web app can be migrated to Azure PaaS given enough time and effort. This checklist can be used to assess an App in the early stages of a migration project. It is a list of common technical scoping questions that an engineer may ask.

The checklist on this page is for a .NET Framework _rehost_ scenario:

* .NET Framework 3.5 or greater
* Microsoft SQL Server version 2008 R2 or greater
* Target state is Windows App Service Plans / App Service Environments (not Cloud Services, VMSS, AKS, Containers, Linux, IIS VMs)
* Target state is Azure SQL DB or Azure SQL MI (not SQL Server VMs)

## Current state

What is currently deployed and where. What are the dependencies.

> 💡 **[Azure Migration Center]** offers resources, tools and programmes for evaluating and performing Web App Migrations. 

> 💡 Use the **[App Service Migration Assistant]** or a third party tool to scan and generate a report on the current state of the Web App. 

> 📖 Read [Migrate your .NET web app or service to Azure App Service] for an extensive list of App Service migration considerations.

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
1. Any ISAPI filters?
1. File system access?

#### WCF services

1. WCF services used? 
1. Same VM (tier) as Web or separate?
1. HTTPS bindings? Any non HTTP bindings?
1. What type auth?

#### DB tier

1. What version SQL Server?
1. How many VMs, cores. How much RAM per VM?
1. How many DBs and what size?
1. Sharded DBs? Shard master?
1. SQL Server using local Timezone or UTC?
1. SSRS? SSAS? SSIS?

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


## Compatibility Checks

If the answer to any of these questions is yes, some refactoring and/or rearchitecting may be required to make the solution compatible with Azure App Services.

#### Web

1. Any MSI installed components?
1. Any GAC'ed DLLs?
1. Any COM or COM+ components?
1. Any binary references?
1. Only ports 80 and 443 used?

#### DB

1. Any GO statements in SQL?
1. Any cross-DB joins in SQL?
1. Any .NET CLR Functions in SQL?
1. Any SQL MSDTC?

## Business requirements

What are the current vs. target business (non-functional) requirements? 

### Performance

1. Concurrent and total users?
1. Peak requests per minute/second (RPM/RPS)?
1. RPM per (web) core?
1. DB requests per Page request?
 
### Reliability

1. Recovery time objecttive (RTO)?
1. Recovery point objective (RPO)? 
1. System uptime (as percentage), e.g. [99.9%]

## Target State

#### App Services

1. App Service Plan / App Service Environment?


#### Azure SQL

1. Azure SQL DB?
   1. vCore or DTU model>?
   1. Elastic Pool?
1. Azure SQL MI?

## Links & references

* [Introducing the App Service Migration Assistant for ASP.NET applications]
* [App Service Migration Assistant Migration docs]

[Azure Migration Center]:https://azure.microsoft.com/en-us/migration/
[App Service Migration Assistant]:https://appmigration.microsoft.com/
[Migrate your .NET web app or service to Azure App Service]:https://docs.microsoft.com/en-us/dotnet/azure/migration/app-service
[App Service Migration Assistant Migration docs]:https://github.com/Azure/App-Service-Migration-Assistant/tree/master/MigrationDocs
[99.9%]:https://uptime.is/99.9
[Introducing the App Service Migration Assistant for ASP.NET applications]:https://azure.microsoft.com/en-us/blog/introducing-the-app-service-migration-assistant-for-asp-net-applications/