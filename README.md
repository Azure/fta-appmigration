# FastTrack for Azure - App Migration

Advice, links, checklists, task lists and other resources for engineers working on Application Migration projects in Azure.

> ℹ Note that these docs are technical, intended to be read by engineers who are experienced in App migration, and who are overseeing the technical tasks of a migration project. These docs are not exhaustive and may not include information that is important to other project stakeholders.

## About FastTrack for Azure

**FastTrack for Azure** is a team of engineers and program managers who work closely with customers to design, configure and deploy solutions in Azure. Our customers' projects include some of the largest, most complex and most critical workloads deployed into public cloud today. 

Many customers and partners who are migrating applications to Azure will engage the FastTrack for Azure team to assist with their migration. The advice in this repo is based on "real world" experience gained from delivering thousands of engagements and hundreds of successful production deployments in Azure.

> 📖 Visit **[Microsoft FastTrack for Azure]** to learn more about FastTrack

## About AMP for .NET

**Azure Migration Program (AMP)** is a fully managed migration program which offers best-practice guidance, direct access to Azure engineers, tools and subsidized partner services. AMP comes in three flavours: Datacenter (DC) migration, Windows Virtual Desktop (WVD) migration and AMP for .NET.

AMP for .NET will migrate ASP.NET applications from IIS + SQL to Azure App Services to Azure SQL DB. Qualified customers will receive guidance, tools, and work with a Microsoft expert partner to complete their migration project. FastTrack for Azure engineers work in AMP projects to provide advice and guidance directly from Azure Engineering.

> 📖 Visit **[Azure Migration Program]** to learn more about the AMP for .NET program

## Migration phases

In this repo engineers will find advice, checklists and task-lists for each phase of an App migration project. These docs are intended as a guide for experience engineers and partners and are not exhaustive. Wherever possible we have linked to existing docs.

![Flowchart showing example of Migration Phases for an App Migration project](./docs/images/migration-phases.png)<br/>_Figure: Example of Migration Phases for App Migration project_

### Pre-migration

* **[Kickoff & Discovery]**
* **Skilling**
* **[Application Inventory]**
* **[Landing Zone]**

### Migration waves

For-each App + SQL backend:

* **[Prepare]**
* **[Modernize]**
* **[Test & validate]**
* **[Production deploy]**

### Post-migration

* **[Post go-live support]**

## Links & references

* [Migrate your .NET web app or service to Azure App Service]
* [Introducing the App Service Migration Assistant for ASP.NET applications]
* [App Service Migration Assistant Migration docs]
* <https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/reference/fundamental-concepts/hosting-hierarchy>
* <https://docs.microsoft.com/en-us/azure/architecture/example-scenario/gateway/firewall-application-gateway>
* <https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree>

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Legal Notices

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.

Privacy information can be found at https://privacy.microsoft.com/en-us/

Microsoft and any contributors reserve all other rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.

<!-- LINKS -->
[Azure Migration Program]:https://azure.microsoft.com/en-us/migration/migration-program/
[Microsoft FastTrack for Azure]:https://azure.microsoft.com/en-us/programs/azure-fasttrack/
[Kickoff & Discovery]:./docs/discovery.md
[Application Inventory]:./docs/app-inventory.md
[Landing Zone]:./docs/landing-zone.md
[Prepare]:./docs/prepare.md
[Modernize]:./docs/modernize.md
[Test & validate]:./docs/testing-validation.md
[Production deploy]:./docs/prod-deploy.md
[Post go-live support]:./docs/support.md
[Migrate your .NET web app or service to Azure App Service]:https://docs.microsoft.com/en-us/dotnet/azure/migration/app-service
[App Service Migration Assistant Migration docs]:https://github.com/Azure/App-Service-Migration-Assistant/tree/master/MigrationDocs
[99.9%]:https://uptime.is/99.9
[Introducing the App Service Migration Assistant for ASP.NET applications]:https://azure.microsoft.com/en-us/blog/introducing-the-app-service-migration-assistant-for-asp-net-applications/
