[[_TOC_]]

## 1.0 Abstract

Naming standard includes HTSS corporate part and recommended [Microsoft Naming](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming) standards.

Naming convention define standard names for devices, components and resources connected to network in HTSS and is mandatory for all resources entities in holding. This document will introduce our implementation with examples.

An effective naming convention consists of resource names from important information about each resource. A good name helps you quickly identify the resource's type, associated workload, environment, and the Azure region hosting it.

## 2.0 Custom Enumerations
### 2.1 Organization enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| High Tech Systems & Software | `htss` |

### 2.2 Business unit enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| Custom software development | `csd` |
| Product development | `prd` |
| IT academy and trainings | `iat` |

### 2.3 Country enumerations - ISO-3166 alpha 2

| __Full name__ | __Abbreviation__ |
|--|--|
| Global services | `gl` |
| Roumania | `ro` |
| Czech | `cz` |
| Poland | `pl` |
| Italy | `it`|
| Serbia | `rs` |
| Hungary | `hu` |
| Slovakia | `sk` |
| Bulgaria | `bg`|

__[Full ISO 3166 Country Codes](https://www.iso.org/obp/ui/#search)__

### 2.4 Location enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| North Europe | `ne` |
| West Europe | `we` |

### 2.5 Environment enumerations

| __Full name__ | __Abbreviation long__ | __Abbreviation short__ |
|--|--|--|
| Development | `dev` | `d` |
| Integration | `int` | `i` |
| User Acceptance Testing | `uat` | `u` |
| Testing | `test` | `t` |
| Pre-production | `pre` | `r` |
| Production | `prod` | `p` |
| Demonstration | `demo` | `e` |

### 2.6 Billing license enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| Enterprise agreement | `ea` |
| Cloud Solution Provider | `csp` |
| MCA | `mca` |
| New Commerce Experience (replacement of CSP) | `nce` |

### 2.7 VM type enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| Workstation | `ww` |
| Windows server | `ws` |
| Linux server | `ls` |
| Scale set | `ss` |
| Unix server | `us` |
| Windows virtual desktop | `wd` |
| Container | `cn` |

### 2.8 Project Enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| Poseidon | `ps` |
| Shiftin | `sh` |
| MindClass | `mc` |
| Columbus | `cb` |
| TBD |

### 2.9 Service/Roles Enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| Consul | `csl` |
| RabbitMQ | `rmq` |
| Elastic Search | `els` |
| SonarQube | `snq` |
| Web Services | `web` |
| Redis | `red` |
| TBD | 


## 3.0 Patterns

Only standard english alphanumeric characters [a-z], numbers [0-9] and approved delimiters [dash, space, comma or dot] are used for Azure objects names and attributes described in this document. No other characters are allowed. Some standard characters are not allowed on the names in Azure. __All characters lowercase - no exception.__

### 3.1 Conditions:

- Only standard english alphanumeric characters
- Lowercase in all main parent resource types
- Valid characters & delimiters:
> - a through z (lowercaseletters)
> - 0 through 9 (numbers)
> - dash, space, comma or dot
- Length and character limits - [Resource naming restrictions - Azure Resource Manager | Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules)
- Use standard abbreviations as described in [Azure Abbreviations for resource types](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) on Microsoft Azure best practices KB regarding naming conventions


### 3.2 General pattern

Following the given enumerations, standard abbreviations and the pattern conditions, the table below can be used as guide as generic referral for resource types that won't be defined explicitly as example in this document.

__Exceptions__ will have dedicated naming convention, because of name length limitations in resource name imposed by Microsoft. Resource objects below will have their own specific table as will be shown below in the document:
>- __Management Groups__
>- __Subscriptions__
>- __VMs__
>- __Storage Accounts__
>- __Key Vaults__
>- [__Azure Container Registry__](#excr)

This table is valid as __generic pattern__ and it can be used for __AI + machine learning, Analytics and IoT, Compute and Web, Containers, Databases, Integration, Management and governance, Networking and other remaining topics__:

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ | __Note__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | letters based on [abbreviation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) | `rg` | An abbreviation that represents the type of Azure resource or asset.  |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | The region where the resource is deployed. |
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project, application or service | `yes` | letters and numbers | `phoebe` | Unique name of a project, application, or service that the resource is a part of. |
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` | The stage of the development lifecycle for the workload that the resource supports. |
| \#10| Instance | `yes` | number | `001` | The instance count for a specific resource to identify more than one resource that has the same naming convention. |

__`gl-rg-phoebe-prod001`__
__`gl-mysql-phoebe-prod001`__
__`gl-aks-phoebe-prod001`__


### 3.3 Examples
In the example tables below can be found the most common resources and will guide you how to proceed with naming selection. Consult full list of abbreviations that can be used for `#3` Resource type at the end of each chapter.

#### 3.3.1 AI + machine learning
| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `srch` - Azure Cognitive search<br>`cog` - Azure Cognitive Services<br>`mlw` - Azure Machine Learning Workspace<br>| `mlw` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-mlw-ne-phoebe-prod001`__

<details>
<summary>
[AI + Machine learning abbreviations - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation|
|--|--|--|
|Azure Cognitive Search|Microsoft.Search/searchServices|srch|
|Azure Cognitive Services|Microsoft.CognitiveServices/accounts|cog|
|Azure Machine Learning workspace|Microsoft.MachineLearningServices/workspaces|mlw|
</details>

___

#### 3.3.2 Analytics and IoT

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `adf` - Azure Data Factory<br>`asa` - Azure Stream Analytics<br>`evh` - Event Hub<br>`hbase` - HD Insight - HBase cluster<br>`hadoop` - HD Insight - Hadoop cluster<br>`spark` - HD Insight - Spark cluster<br>`iot` - IoT Hub<br>`pbi` - Power BI Embedded| `adf` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`gl-adf-ne-phoebe-prod001`__
__`gl-hadoop-ne-phoebe-dev001`__
__`cz-iot-we-phoebe-test001`__

<details>
<summary>
[Analytics and IoT abbreviations - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation|
|--|--|--|
|Azure Analysis Services server|Microsoft.AnalysisServices/servers|as|
|Azure Databricks workspace|Microsoft.Databricks/workspaces|dbw|
|Azure Data Explorer cluster|Microsoft.Kusto/clusters|dec|
|Azure Data Explorer cluster database|Microsoft.Kusto/clusters/databases|dedb|
|Azure Data Factory|Microsoft.DataFactory/factories|adf|
|Azure Digital Twin instance|Microsoft.DigitalTwins/digitalTwinsInstances|dt|
|Azure Stream Analytics|Microsoft.StreamAnalytics/cluster|asa|
|Azure Synapse Analytics Workspaces|Microsoft.Synapse/workspaces|synw|
|Azure Synapse Analytics SQL Dedicated Pool|Microsoft.Synapse/workspaces/sqlPools|syndp|
|Azure Synapse Analytics Spark Pool|Microsoft.Synapse/workspaces/sqlPools|synsp|
|Data Lake Store account|Microsoft.DataLakeStore/accounts|dls|
|Data Lake Analytics account|Microsoft.DataLakeAnalytics/accounts|dla|
|Event Hubs namespace|Microsoft.EventHub/namespaces|evhns|
|Event hub|Microsoft.EventHub/namespaces/eventHubs|evh|
|Event Grid domain|Microsoft.EventGrid/domains|evgd|
|Event Grid subscriptions|Microsoft.EventGrid/eventSubscriptions|evgs|
|Event Grid topic|Microsoft.EventGrid/domains/topics|evgt|
|Event Grid system topic|Microsoft.EventGrid/systemTopics|egst|
|HDInsight - Hadoop cluster|Microsoft.HDInsight/clusters|hadoop|
|HDInsight - HBase cluster|Microsoft.HDInsight/clusters|hbase|
|HDInsight - Kafka cluster|Microsoft.HDInsight/clusters|kafka|
|HDInsight - Spark cluster|Microsoft.HDInsight/clusters|spark|
|HDInsight - Storm cluster|Microsoft.HDInsight/clusters|storm|
|HDInsight - ML Services cluster|Microsoft.HDInsight/clusters|mls|
|IoT hub|Microsoft.Devices/IotHubs|iot|
|Provisioning services|Microsoft.Devices/provisioningServices|provs|
|Provisioning services certificate|Microsoft.Devices/provisioningServices/certificates|pcert|
|Power BI Embedded|Microsoft.PowerBIDedicated/capacities|pbi|
|Time Series Insights environment|Microsoft.TimeSeriesInsights/environments|tsi|
</details>

___

#### 3.3.3 Compute and Web

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `app` - WebApp<br>`func` - Function App<br>`cld` - Cloud Service<br>`ntfns` - Notification Hubs Namespace<br>| `func` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`ro-func-ne-phoebe-dev001`__
__`gl-app-ne-phoebe-prod001`__
__`gl-asp-ne-phoebe-prod001`__
__`pl-ase-phoebe-test001`__
__`gl-gal-phoebe-prod012`__

<details>
<summary>
[Compute and Web abbreviations - Complete list]</summary>
<br>

|__Resource__|__Resource provider namespace__|__Abbreviation__|
|--|--|--|
|App Service environment|Microsoft<span><span>.</span></span>Web/hostingEnvironments|ase|
|App Service plan|Microsoft<span><span>.</span></span>Web/serverFarms|asp|
|Azure Load Testing instance|Microsoft<span>.</span>LoadTestService/loadTests|lt|
|Availability set|Microsoft<span>.</span>Compute/availabilitySets|avail|
|Azure Arc enabled server|Microsoft<span>.</span>HybridCompute/machines|arcs|
|Azure Arc enabled Kubernetes cluster|Microsoft<span>.</span>Kubernetes/connectedClusters|arck|
|Batch accounts|Microsoft<span>.</span>Batch/batchAccounts|ba|
|Cloud service|Microsoft<span>.</span>Compute/cloudServices|cld|
|Communication Services|Microsoft<span>.</span>Communication/communicationServices|acs|
|Function app|Microsoft<span>.</span>Web/sites|func|
|Gallery|Microsoft<span>.</span>Compute/galleries|gal|
|Hosting environment|Microsoft<span>.</span>Web/hostingEnvironments|host|
|Image template|Microsoft<span>.</span>VirtualMachineImages/imageTemplates|it|
|Notification Hubs|Microsoft<span>.</span>NotificationHubs/namespaces/notificationHubs|ntf|
|Notification Hubs namespace|Microsoft<span>.</span>NotificationHubs/namespaces|ntfns|
|Proximity placement group|Microsoft<span>.</span>Compute/proximityPlacementGroups|ppg|
|SNAPshot|Microsoft<span>.</span>Compute/snapshots|SNAP|
|Static web app|Microsoft<span>.</span>Web/staticSites|stapp|
|Web app|Microsoft<span>.</span>Web/sites|app|
</details>

___

#### 3.3.4 Containers

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `aks` - AKS Cluster<br>`ca` - Container Apps<br>`ci` - Container Instance | `aks` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-aks-ne-phoebe-prod001`__
__`ro-ca-ne-phoebe-test002`__
__`gl-aks-ne-phoebe-dev003`__
__`bg-ci-we-phoebe-uat005`__

<a id="excr"></a>__Except Azure Container Registry, supports only Alphanumeric characters (no hyphens)__, we are simpy removing the hyphens:
__`glcrwephoebeprod004`__

<details>
<summary>
[Containers abbreviations - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation|
|--|--|--|
|AKS cluster|Microsoft.ContainerService/managedClusters|aks|
|Container apps|Microsoft.App/containerApps|ca|
|Container apps environment|Microsoft.App/managedEnvironments|cae|
|Container registry|Microsoft.ContainerRegistry/registries|cr|
|Container instance|Microsoft.ContainerInstance/containerGroups|ci|
|Service Fabric cluster|Microsoft.ServiceFabric/clusters|sf|
|Service Fabric managed cluster|Microsoft.ServiceFabric/managedClusters|sfmc|
</details>

___

#### 3.3.5 Databases
| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `sql` - Azure SQL Database server<br>`sqldb` - Azure SQL Database<br>`cosmos` - Azure Cosmos DB<br> `redis` - Azure Cache for Redis<br>`mysql` - MySQL DB<br>`psql` - PostgresSQL DB <br>`sqlstrdb` - Azure SQL Server Strech DB<br>`sqlmi` - Azure SQL Managed Instance<br>| `sql`
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-sql-ne-phoebe-prod001`__
__`gl-sqldb-ne-phoebe-prod001`__
__`gl-mysql-ne-phoebe-dev003`__

<details>
<summary>
[Database abbreviations - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation
|--|--|--|
|Azure Cosmos DB database|Microsoft.DocumentDB/databaseAccounts/sqlDatabases|cosmos|
|Azure Cosmos DB for Apache Cassandra account|Microsoft.DocumentDB/databaseAccounts|coscas|
|Azure Cosmos DB for MongoDB account|Microsoft.DocumentDB/databaseAccounts|cosmon|
|Azure Cosmos DB for NoSQL account|Microsoft.DocumentDb/databaseAccounts|cosno|
|Azure Cosmos DB for Table account|Microsoft.DocumentDb/databaseAccounts|costab|
|Azure Cosmos DB for Apache Gremlin account|Microsoft.DocumentDb/databaseAccounts|cosgrm|
|Azure Cosmos DB PostgreSQL cluster|Microsoft.DBforPostgreSQL/serverGroupsv2|cospos|
|Azure Cache for Redis instance|Microsoft.Cache/Redis|redis|
|Azure SQL Database server|Microsoft.Sql/servers|sql|
|Azure SQL database|Microsoft.Sql/servers/databases|sqldb|
|Azure SQL Elastic Job agent|Microsoft.Sql/servers/jobAgents|sqlja|
|Azure SQL Elastic Pool|Microsoft.Sql/servers/elasticpool|sqlep|
|MariaDB server|Microsoft.DBforMariaDB/servers|maria|
|MariaDB database|Microsoft.DBforMariaDB/servers/databases|mariadb|
|MySQL database|Microsoft.DBforMySQL/servers|mysql|
|PostgreSQL database|Microsoft.DBforPostgreSQL/servers|psql|
|SQL Server Stretch Database|Microsoft.Sql/servers/databases|sqlstrdb|
|SQL Managed Instance|Microsoft.Sql/managedInstances|sqlmi|
</details>

___

#### 3.3.6 Integration

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `sb` - Service Bus<br>`sbq` - Service Bus queue<br>`sbt` - Service Bus Topic<br> | `sbq` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-sbq-ne-phoebe-prod001`__

<details>
<summary>
[Integration abbreviations - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation|
|--|--|--|
|API management service instance|Microsoft.ApiManagement/service|apim|
|Integration account|Microsoft.Logic/integrationAccounts|ia|
|Logic apps|Microsoft.Logic/workflows|logic|
|Service Bus namespace|Microsoft.ServiceBus/namespaces|sbns|
|Service Bus queue|Microsoft.ServiceBus/namespaces/queues|sbq|
|Service Bus topic|Microsoft.ServiceBus/namespaces/topics|sbt|
|Service Bus topic subscription|Microsoft.ServiceBus/namespaces/topics/subscriptions|sbts|
</details>

___

#### 3.3.7 Management and governance

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `aa` - Automation account<br>`appi` - Application Insights<br>`log` - Log Analytics workspace<br>`rg` - Resource group | `appi` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-appi-ne-phoebe-prod001`__
__`ro-law-ne-phoebe-test003`__
__`pl-rg-ne-phoebe-dev005`__

<details>
<summary>
[Management and governance abbreviations  - Complete list]</summary>
<br>

|Resource|Resource provider namespace|Abbreviation
|--|--|--|
|Automation account|Microsoft.Automation/automationAccounts|aa|
|Azure Policy definition|Microsoft.Authorization/policyDefinitions|<descriptive>|
|Application Insights|Microsoft.Insights/components|appi|
|Azure Monitor action group|Microsoft.Insights/actionGroups|ag|
|Azure Monitor data collection rules|Microsoft.Insights/dataCollectionRules|dcr|
|Blueprint|Microsoft.Blueprint/blueprints|bp|
|Blueprint assignment|Microsoft.Blueprint/blueprints/artifacts|bpa|
|Log Analytics workspace|Microsoft.OperationalInsights/workspaces|log|
|Log Analytics query packs|Microsoft.OperationalInsights/querypacks|pack|
|Management group|Microsoft.Management/managementGroups|mg|
|Microsoft Purview instance|Microsoft.Purview/accounts|pview|
|Resource group|Microsoft.Resources/resourceGroups|rg|
|Template specs name|Microsoft.Resources/templateSpecs|ts|
</details>

___

#### 3.3.8 Networking

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `vnet` - Virtual Network<br>`snet` - Subnet<br>`pep` - Private Endpoint<br>`pip` - Public IP Address<br>`lbi` - Internal Load Balancer<br>`lb` - General Load Balancer<br> `lbe` - External Load Balancer<br>`nsg` - Network Security Group<br>`lgw` - Local Network Gateway <br>`vgw` - Virtual Network Gateway<br>`rt` - Route Table | `vnet` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-vnet-ne-phoebe-prod001`__
__`gl-lbi-ne-phoebe-prod001`__
__`gl-snet-ne-phoebe-dev003`__
__`cs-nsg-ne-phoebe-prod001`__
__`gl-udr-ne-phoebe-test002`__

<details>
<summary>
[Networking abbreviations - Complete list]</summary>
<br>

|Resource|Resourceprovider namespace|Abbreviation|
|--|--|--|
|Application gateway|Microsoft.Network/applicationGateways|agw|
|Application security group (ASG)|Microsoft.Network/applicationSecurityGroups|asg|
|CDN profile|Microsoft.Cdn/profiles|cdnp|
|CDN endpoint|Microsoft.Cdn/profiles/endpoints|cdne|
|Connections|Microsoft.Network/connections|con|
|DNS|Microsoft.Network/dnsZones|<DNS domain name>|
|DNS private resolver|Microsoft.Network/dnsResolvers|dnspr|
|DNS private resolver inbound endpoint|Microsoft.Network/dnsResolvers/inboundEndpoints|in|
|DNS private resolver outbound endpoint|Microsoft.Network/dnsResolvers/outboundEndpoints|out|
|DNS zone|Microsoft.Network/privateDnsZones|<DNS domain name>|
|Firewall|Microsoft.Network/azureFirewalls|afw|
|Firewall policy|Microsoft.Network/firewallPolicies|afwp|
|ExpressRoute circuit|Microsoft.Network/expressRouteCircuits|erc|
|Front Door (Standard/Premium) profile|Microsoft.Cdn/profiles|afd|
|Front Door (Standard/Premium) endpoint|Microsoft.Cdn/profiles/afdEndpoints|fde|
|Front Door firewall policy|Microsoft.Network/frontdoorWebApplicationFirewallPolicies|fdfp|
|Front Door (classic)|Microsoft.Network/frontDoors|afd|
|Load balancer (general)|Microsoft.Network/loadBalancers|lb|
|Load balancer (internal)|Microsoft.Network/loadBalancers|lbi|
|Load balancer (external)|Microsoft.Network/loadBalancers|lbe|
|Load balancer rule|Microsoft.Network/loadBalancers/inboundNatRules|rule|
|Local network gateway|Microsoft.Network/localNetworkGateways|lgw|
|NAT gateway|Microsoft.Network/natGateways|ng|
|Network interface (NIC)|Microsoft.Network/networkInterfaces|nic|
|Network security group (NSG)|Microsoft.Network/networkSecurityGroups|nsg|
|Network security group (NSG) security rules|Microsoft.Network/networkSecurityGroups/securityRules|nsgsr|
|Network Watcher|Microsoft.Network/networkWatchers|nw|
|Private Link|Microsoft.Network/privateLinkServices|pl|
|Private endpoint|Microsoft.Network/privateEndpoints|pep|
|Public IP address|Microsoft.Network/publicIPAddresses|pip|
|Public IP address prefix|Microsoft.Network/publicIPPrefixes|ippre|
|Route filter|Microsoft.Network/routeFilters|rf|
|Route server|Microsoft.Network/virtualHubs|rtserv|
|Route table|Microsoft.Network/routeTables|rt|
|Service endpoint policy|Microsoft.serviceEndPointPolicies|se|
|Traffic Manager profile|Microsoft.Network/trafficManagerProfiles|traf|
|User defined route (UDR)|Microsoft.Network/routeTables/routes|udr|
|Virtual network|Microsoft.Network/virtualNetworks|vnet|
|Virtual network peering|Microsoft.Network/virtualNetworks/virtualNetworkPeerings|peer|
|Virtual network subnet|Microsoft.Network/virtualNetworks/subnets|snet|
|Virtual WAN|Microsoft.Network/virtualWans|vwan|
|Virtual network gateway|Microsoft.Network/virtualNetworkGateways|vgw|
</details>

___

#### 3.3.9 Security

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `bas` - Azure Bastion<br>`id` - Managed Identity<br>`vpng` - VPN Gateway<br>`vcn` - VPN Connection<br>`vst` - Site-to-site connection<br>`waf` - Web Application Firewall (WAF) policy<br>`wafrg` - Web Application Firewall (WAF) policy rule group | `vcn` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Project | `yes` | letters and numbers | `phoebe` | 
| \#8 | Delimiter |  | 1 dash | `-` |  |
| \#9 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#10| Instance | `yes` | number | `001` | 

__`gl-vcn-ne-phoebe-prod001`__
___

#### 3.3.10 Others [ * ]

Resource Types that are not tied up to this document are:
- [Developer Tools](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations#developer-tools)
- [DevOps](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations#devops)
- [Migration](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations#migration)
- [Virtual desktop infrastructure](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations#virtual-desktop-infrastructure)

_* these Resource Types follow the same general pattern with it's associated abbreviations._

___

### 3.4 Exceptions

#### 3.4.1 Management Groups

Management groups are not following the generic pattern as their structure is strictly defined and won't be changed for a long time period. Management group names are strings consists of lowercase english only characters, numbers and dash could be used as delimiter to enhance the readability.

>- htss
>- landing-zones
>- management
>- identity-service

___

#### 3.4.2 Subscriptions

Unlike the general pattern, Subscriptions needs to be identified by Organization and it's Billing associated License. Subscriptions will be defined with properties from the [Organization enumeration](#user-content-2.1-organization-enumerations) and [Billing license enumerations](#user-content-2.6-billing-license-enumerations).

_* general [conditions](#user-content-3.1-conditions%3A) are propagated to Subscriptions naming convention_

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Organization | `yes` | [enumeration](#user-content-2.1-organization-enumerations) | `htss` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | (Common) Resource types | `yes` | `sub` - Subscription<br> | `sub` |
| \#6 | Delimiter |  | 1 dash | `-` |  |
| \#7 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`htss-gl-sub-ne-phoebe-prod001`__
__`htss-ro-sub-ne-phoebe-test001`__
__`htss-gl-sub-we-phoebe-dev001`__

___

#### 3.4.3 Virtual Machines

Azure virtual machines have two distinct names: resource name and host name. When you deploy a virtual machine, the same value is used for both names. The restrictions regarding the name maxlimit characters are for the host name. The actual resource name can have up to 64 characters (Linux based VMs) and up to 15 characters (Windows Based VMs). VM names for htss organization will have maximum of 15 characters (no matter the base layer OS) for symmetry, management and governance (ADDS, AAD, SCCM, Intune, etc) purposes and we're going to stick to the conditions below.

__Contitions:__
- Only standard english alphanumeric characters
- Strictly lowercase in all main parent resource types
- Can't use spaces, control characters, or these characters:
>- `~ ! @ # $ % ^ & * ( ) = + _ [ ] { } \ | ; : . ' " , < > / ?`
- Length is 15 characters max
- Abbbreviations will be consumed from [2.6 VM type enumerations](#user-content-2.6-vm-type-enumerations)
- Each naming order will have limited number of characters as shown in example table below

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `ww` - Workstation<br>`ws` - Windows Server<br>`ls` - Linux Server<br>`ss` - Scale Set<br>`us` - Unix Server<br>`wd` - Windows virtual desktop<br>`cn` - Container | 2 | `ls` |
| \#3 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Project short form | `yes` | [project enumeration](#user-content-2.8-project-enumerations) | 2 | __`ps`__ |
| \#5 | Project count | `yes` | numeric string | 1 | `1` |
| \#6 | Role short form | `yes` | [service/roles enumeration](#user-content-2.9-service/roles-enumerations) | 3 | __`rmq`__ | 
| \#7 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#8| Instance count | `yes` | numeric string | 2 | `01` | 

__`gllsneps1rmqp01`__
__`rowsnesh1cslp02`__
__`czlsnemc1webp01`__
__`plwsnecb1elsd03`__
__`bglsnecb1elsd23`__

___

#### 3.4.4 Storage accounts

Storage account family do not follow generic pattern as they have naming length restrictions imposed by Microsoft. Global scoped Storage Accounts must be 24 characters. Given this condition we are going to apply the same naming policies for storage resources in the following table.

__Contitions:__
- Only standard english alphanumeric characters
- Strictly lowercase in all resource types
- Can't use spaces, control characters, or these characters:
>- `~ ! @ # $ % ^ & * ( ) = + _ [ ] { } \ | ; : . ' " , < > / ?`
- Length is 24 characters max
- Each naming order will have limited number of characters as shown in example table below

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `st` - Storage Account<br>`stdiag` - Storage Account for diagnostic logs<br> `ssimp` -  Azure StorSimple<br> `dla` - Data Lake Analytics<br> `dls` - Data Lake Storage Account<br> `savm` - Virtual Machine Storage account<br>`bvault` - Backup Vault Name<br> `bkpol` - Backup Vault Policy<br>`share` - File Share | 2-6 | `stdiag` |
| \#3 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Project | `yes` | letters and numbers | 10-14 | __`phoebe`__ | 
| \#5 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#6| Instance | `yes` | number | 3 | `001` | 

__`glstdiagnephoebep001`__
__`glstnephoebep001`__
__`glstnephoebet003`__
__`csstiagnephoebet012`__
__`prstnephoebed003`__

___

#### 3.4.5 Key Vaults

Key Vaults are following the same conditions as [Storage Accounts](#user-content-3.4.4-storage-accounts), the resource naming needs to be 24 characters long imposed by Microsoft.

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [enumeration](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `kv` - Key Vault | 2 | `kv` |
| \#3 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Project | `yes` | letters and numbers | 14 | __`phoebe`__ | 
| \#5 | Environment | `yes` | [enumeration](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#6| Instance | `yes` | number | 3 | `001` | 

__`glkvnephoebep001`__
__`cskvnephoebed003`__
__`iakvnephoebet002`__

___

#### 3.4.6 Azure Container Registries

See [__Azure Container Registry__](#excr).

#### 3.4.7 Dependent resources

##### 3.4.7.1 VM Associations

Resources that are attached/associated to VMs needs to have good visibility especially when you are reading the information from IaC deployment type of files. We are going to have all child (dependent) resources with __upper case letters__. 

`%vm_name%`-__OS-DISK001__
`%vm_name%`-__DATA-DISK001__

<details>
<summary>
[VM Disks Examples - More]</summary>
<br>

__`gllsnepsrmqp6y2`__-OS-DISK001
__`gllsnepsrmqp6y2`__-DATA-DISK001
__`gllsnepsrmqp6y2`__-DATA-DISK002
__`czlsnemcwebp7kc`__-OS-DISK001
__`plwsnecbelsd7fg`__-OS-DISK001
__`plwsnecbelsd7fg`__-OS-DISK002
</details>
<br>

For snapshots the same inheritance principle must follow. The snapshots __do not inherit the VM name__ but the disk full name followed by dash delimiter `-`, it's abbreviation `SNAP` and a count index that starts at `001` and counts up with every SNAPshot created.

`%disk_name%`-__SNAP001__
`%disk_name%`-__SNAP002__

<details>
<summary>
[VM Disk snapshots Examples - More]</summary>
<br>

__`gllsnepsrmqp6y2`__-OS-DISK001-SNAP001
__`gllsnepsrmqp6y2`__-OS-DISK001-SNAP002
__`gllsnepsrmqp6y2`__-DATA-DISK001-SNAP001
__`gllsnepsrmqp6y2`__-DATA-DISK002-SNAP001
__`czlsnemcwebp7kc`__-OS-DISK001-SNAP001
__`plwsnecbelsd7fg`__-OS-DISK001-SNAP001
__`plwsnecbelsd7fg`__-OS-DISK002-SNAP001
</details>

##### 3.4.7.2 VM Network Interface Card

Network Interface Cards that are attached/associated with VMs will follow the same inheritance theory against the parent VMs that they are being connected to followed by dash delimiter `-`, it's abbreviation `nic` and a count index that starts at `001` and counts up. 

`%vm_name%`-__NIC001__

<details>
<summary>
[VM NIC Examples - More]</summary>
<br>

__`plwsnecbelsd7fg`-NIC001__
__`plwsnecbelsd7fg`-NIC002__
__`plwsnecbelsd7fg`-NIC003__
__`czlsnemcwebp7kc`-NIC001__
</details>

___

### 4.0 Tagging strategy

Tags will be applied to subscription and resource group level. Subscription tags will be stand-alone tagging configuration while Resource Grup mandatory tags will be propagated to each resource inside of it (policies will take care of the propagation). Each resource can have optional tags. Tagging strategy is following the model below:

- __Subscription__ tagging model

|__Tag Key__|__Value Format__|__Example__|__Mandatory__|
|--|--|--|--|
|costCenter|[2.2 Country Code enumerations](#user-content-2.3-country-enumerations---iso-3166-alpha-2)|Product Development|yes|
|projectName|string|Phoebe|yes|
|projectID|project identificator|HTSS|yes|
|environment|[2.4 Environment enumerations](#user-content-2.5-environment-enumerations)|PROD|yes|
|owner|AAD principal name|john.doe@htss.ro|yes|

<br>

- __Resource Group__ tagging model

|__Tag Key__|__Value Format__|__Example__|__Mandatory__|
|--|--|--|--|
|projectName|string|Phoebe|yes|
|projectID|project identificator|HTSS|yes|
|bussinessUnit|[2.2 Business Unit](#user-content-2.2-business-unit-enumerations) - short|csd|yes|
|environment|[2.5 Environment enumerations](#user-content-2.5-environment-enumerations)|PROD|yes|
|owner|AAD principal name|john.doe@htss.ro|yes|
|description|Small project description/scope|testing terraform for Phoebe|yes|


<br>

- __Resource object__ standalone optional tags

Each resource can have optional tags that can be added in addition to the mandatory tags.

|__Tag Key__|__Value Format__|__Example__|__Mandatory__|
|--|--|--|--|
|country|[Geographical Location ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2)|RO|no|
|role|description of service role|consul<br>elastic<br>web server<br>rabbitmq<br>java framework<br>etc|no|

____

### 5.0 Summary

Most of the Azure resources in HTSS org will use the general (aka generic pattern). The principal aim of the naming convention is to give us as much information as possible just by reading the name. 

- __Generic__ pattern overview:

|__gl__|-|__sql__|-|__ne__|-|__phoebe__|-|__prod__|__001__|
|--|--|--|--|--|--|--|--|--|--|
|Country Code|-|Resource type|-|Azure Region|-|Project/Service|-|Env type|Instance count|
|Global Serice|-|SQL Server|-|North Europe|-|Phoebe Project|-|Productive System|Instance 001|


- Exception pattern overview:
>- No dashes, character limitation in Project/Service, Env Type using short form, 15 characters VMs, 24 characters Storage Accounts & KeyVaults

VM
|__gl__|__ls__|__we__|__ps__|__csl__|__p__|__001__|
|--|--|--|--|--|--|--|
|Global Service|Linux Server|West Europe|Poseidon Project|Consul|Production|Instance 001|
|2|2|2|2|3|1|3

Others
|__gl__|__kv__|__we__|__phoebe__|__p__|__001__|
|--|--|--|--|--|--|
|Global Service|Key Vault|West Europe|Phoebe Project|Production|Instance 001|


We are integrating our definition of naming convention with Microsoft references regarding this topic. We rely our abbreviations on Microsoft's examples to which we added some small exceptions while also taking into consideration the length limit and character restrictions.

____












