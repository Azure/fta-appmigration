# Application modernization

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