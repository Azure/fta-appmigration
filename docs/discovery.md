# Discovery

Almost any web app can be migrated to Azure PaaS given enough time and effort. This checklist can be used to assess an App in the early stages of a migration project. It is a list of common technical scoping questions that an engineer may ask.

## Current state

What is currently deployed and where? What are the dependencies?

> 💡 **[Azure Migration Center]** offers resources, tools and programmes for evaluating and performing Web App Migrations. 

#### Environments

1. On-prem | Another Cloud | Azure VMs?
1. Which region / geographic area?
1. How many environments? e.g. Dev/Test, UAT, Prod

#### Web tier

1. What versions .NET Framework?
1. More than one Web VM node?
1. Load balancer?
1. How many VMs, cores. How much RAM per VM?
1. How many apps / websites in total?
1. VMs have single role or are shared with SQL/WCF/Windows Services/Other?

#### WCF services

1. WCF services used? 
1. Same VM (tier) as Web or separate?
1. Any non HTTP bindings?

#### DB tier

1. What version SQL Server?
1. How many VMs, cores. How much RAM per VM?
1. How many DBs and what size?
1. SQL Server using local Timezone or UTC?
1. SSRS? SSAS? SSIS?

#### Networking & Security

1. Are websites private (internal / intranet) or public?
1. DMZ?
1. WAF? Audit or Block?
1. Connectivity to on-prem services?
1. Firewall?
1. DDOS?

#### IAM

1. How are users Authenticated?
1. How are users Authorized?

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
1. Any FILESTREAM?

## Business requirements

What are the current vs. target business (non-functional) requirements? 

### Performance

1. Concurrent and total users?
1. Peak requests per minute/second (RPM/RPS)?
1. Current CPU and RAM utilization on VMs at peak load?
1. Current SQL VM IOPS at peak load?
 
### Reliability

1. Recovery time objecttive (RTO)?
1. Recovery point objective (RPO)? 
1. System uptime (as percentage), e.g. [99.9%]

## Target State

#### App Services

1. App Service Plan / App Service Environment?

#### Azure SQL

1. Azure SQL DB?
   1. vCore or DTU model?
   1. Elastic Pool?
1. Azure SQL MI?


[Azure Migration Center]:https://azure.microsoft.com/en-us/migration/
[App Service Migration Assistant]:https://appmigration.microsoft.com/
[Database Migration Assistant]:https://datamigration.microsoft.com/scenario/sql-to-azuresqldbmi?step=1