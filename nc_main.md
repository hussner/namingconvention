[[_TOC_]]

## 1.0 Abstract

The naming standard includes HTSS corporate part and recommended [Microsoft Naming](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming) standards.

The naming convention defines standard names for devices, components and resources connected to the Azure network in HTSS tenant and is mandatory for all resource entities in holding. This document will introduce our implementation with examples.

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

### 2.10 Customer/Client enumerations

| __Full name__ | __Abbreviation__ |
|--|--|
| HTSS| `htss` |
| DrMax| `drm` |
| Amethyst | `ame` |
| Darevo | `drv` |
| EduNet | `edn` |
| Brahms | `brh` |
| Multiple Clients/Managed service| `shared` or `shr`|
| TBD | 

## 3.0 Patterns

Only standard English alphanumeric characters [a-z], numbers [0-9] and approved delimiters [dash, space, comma or dot] are used for Azure objects names and attributes described in this document. No other characters are allowed. Some standard characters are not allowed on the names in Azure. __All characters lowercase for main nondependent resources - no exception.__

### 3.1 Conditions:

- Only standard English alphanumeric characters
- Lowercase in all main parent resource types
- Valid characters & delimiters:
> - a through z (lowercase letters)
> - 0 through 9 (numbers)
> - dash, space, comma or dot
- Length and character limits - [Resource naming restrictions - Azure Resource Manager | Microsoft Docs](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules)
- Use standard abbreviations as described in [Azure Abbreviations for resource types](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) on Microsoft Azure best practices KB regarding naming conventions


### 3.2 General pattern

Following the given enumerations, standard abbreviations and the pattern conditions, the table below can be used as a guide on generic referral of resource types that won't be defined explicitly as an example in this document.

__Exceptions__ will have a dedicated naming convention, because of name length limitations in resource names imposed by Microsoft. Resource objects below will have their specific table as will be shown in the document:
>- __Management Groups__
>- __Subscriptions__
>- __VMs__
>- __Storage Accounts__
>- __Key Vaults__
>- [__Azure Container Registry__](#excr)
>- __Dependent resources (Disks, NICs, Private Endpoints, etc)__

This table is valid as __generic pattern__ and it can be used for __AI + machine learning, Analytics and IoT, Compute and Web, Containers, Databases, Integration, Management and governance, Networking and other remaining topics__:

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ | __Note__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | letters based on [abbreviation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) | `rg` | An abbreviation that represents the type of Azure resource or asset.  |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | The region where the resource is deployed. |
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Client/Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `drm` | The customer that consumes the product/project/resource. |
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project, application or service | `yes` | letters and numbers | `phoebe` | Unique name of a project, application, or service that the resource is a part of. |
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#12 | Delimiter |  | 1 dash | `-` |  |
| \#13 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` | The stage of the development lifecycle for the workload that the resource supports. |
| \#14| Instance | `yes` | number | `001` | The instance count for a specific resource to identify more than one resource that has the same naming convention. |

__`gl-rg-ne-drm-phoebe-databases-prod001`__
__`gl-rg-ne-drm-phoebe-k8s-prod001`__
__`gl-rg-ne-drm-phoebe-webapps-prod001`__
__`gl-rg-ne-drm-phoebe-networking-prod001`__
__`gl-mysql-ne-ame-phoebe-prod001`__
__`gl-aks-ne-shared-phoebe-prod001`__


### 3.3 Examples
In the following example, tables can be found with the most common resources and will guide you on how to proceed with naming selection. Consult full list of abbreviations that can be used for the `#3` Resource type at the end of each chapter.

#### 3.3.1 AI + machine learning
| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `srch` - Azure Cognitive search<br>`cog` - Azure Cognitive Services<br>`mlw` - Azure Machine Learning Workspace<br>| `mlw` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#12 | Delimiter |  | 1 dash | `-` |  |
| \#13 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#14 | Instance | `yes` | number | `001` | 

__`gl-srch-ne-htss-phoebe-ai-prod001`__
__`gl-mlw-ne-shared-phoebe-prod001`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `adf` - Azure Data Factory<br>`asa` - Azure Stream Analytics<br>`evh` - Event Hub<br>`hbase` - HD Insight - HBase cluster<br>`hadoop` - HD Insight - Hadoop cluster<br>`spark` - HD Insight - Spark cluster<br>`iot` - IoT Hub<br>`pbi` - Power BI Embedded| `adf` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`gl-adf-ne-shared-phoebe-store-prod001`__
__`gl-hadoop-ne-drm-phoebe-dataset-dev001`__
__`cz-iot-we-drm-phoebe-test001`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `app` - WebApp<br>`func` - Function App<br>`cld` - Cloud Service<br>`ntfns` - Notification Hubs Namespace<br>| `func` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`ro-func-ne-shared-phoebe-api-dev001`__
__`gl-app-ne-drm-phoebe-php-prod001`__
__`gl-asp-ne-shared-phoebe-nodejs-prod001`__
__`pl-ase-ne-htss-phoebe-asp-test001`__
__`gl-gal-ne-drm-phoebe-linux-prod012`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `aks` - AKS Cluster<br>`ca` - Container Apps<br>`ci` - Container Instance | `aks` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`gl-aks-ne-shared-phoebe-star-prod001`__
__`ro-ca-ne-drm-phoebe-default-test002`__
__`gl-aks-ne-htss-phoebe-dev003`__
__`bg-ci-we-ame-phoebe-uat005`__

<a id="excr"></a>__Except Azure Container Registry, supports only Alphanumeric characters (no hyphens)__, we are simply removing the hyphens:
__`glcrnedrmphoebek8sprod001`__
__`glcrwesharedphoebeprod004`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `sql` - Azure SQL Database server<br>`sqldb` - Azure SQL Database<br>`cosmos` - Azure Cosmos DB<br> `redis` - Azure Cache for Redis<br>`mysql` - MySQL DB<br>`psql` - PostgresSQL DB <br>`sqlstrdb` - Azure SQL Server Strech DB<br>`sqlmi` - Azure SQL Managed Instance<br>| `sql`
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | `ne`  | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#12 | Delimiter |  | 1 dash | `-` |  |
| \#13 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#14 | Instance | `yes` | number | `001` | 

__`gl-sql-ne-shared-phoebe-webapps-prod001`__
__`gl-sql-ne-shared-phoebe-infra-prod001`__
__`gl-sql-ne-shared-phoebe-prod001`__
__`gl-sqldb-ne-drm-phoebe-webapps-prod001`__
__`gl-mysql-ne-ame-phoebe-dev003`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `sb` - Service Bus<br>`sbq` - Service Bus queue<br>`sbt` - Service Bus Topic<br> | `sbq` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12 | Instance | `yes` | number | `001` | 

__`gl-sb-ne-shared-phoebe-topic-prod001`__
__`gl-sbq-ne-shared-phoebe-qs-prod001`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `aa` - Automation account<br>`appi` - Application Insights<br>`log` - Log Analytics workspace<br>`rg` - Resource group | `appi` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12 | Instance | `yes` | number | `001` | 

__`gl-appi-ne-shared-phoebe-vms-prod001`__
__`gl-appi-ne-shared-phoebe-k8s-prod001`__
__`gl-appi-ne-shared-phoebe-webapps-prod001`__
__`ro-law-ne-drm-phoebe-test003`__
__`ro-law-ne-drm-phoebe-k8s-test003`__
__`gl-law-ne-shared-phoebe-sqldb-prod001`__
__`pl-rg-ne-ame-phoebe-dev005`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `vnet` - Virtual Network<br>`snet` - Subnet<br>`pep` - Private Endpoint<br><a id="pip"></a>`pip` - Public IP Address<br>`lbi` - Internal Load Balancer<br>`lb` - General Load Balancer<br> `lbe` - External Load Balancer<br>`nsg` - Network Security Group<br>`lgw` - Local Network Gateway <br>`vgw` - Virtual Network Gateway<br>`rt` - Route Table | `vnet` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`gl-vnet-ne-shared-phoebe-webapps-prod001`__
__`gl-lb-ne-drm-phoebe-infra-prod001`__
__`cz-snet-ne-ame-phoebe-web-dev003`__
__`cz-snet-ne-ame-phoebe-mysql-dev003`__
__`gl-snet-ne-ame-phoebe-st-dev003`__
__`gl_pip_ne_htss-phoebe-lb-prod005`__
__`gl_pip_ne_htss-phoebe-vm-prod001`__
__`ro-nsg-ne-edu-phoebe-snet-prod001`__
__`ro-nsg-ne-edu-phoebe-nic-prod001`__
__`gl-udr-ne-drm-phoebe-test002`__

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
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | Product serves country |
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | (Common) Resource types | `yes` | `bas` - Azure Bastion<br>`id` - Managed Identity<br>`vpng` - VPN Gateway<br>`vcn` - VPN Connection<br>`vst` - Site-to-site connection<br>`waf` - Web Application Firewall (WAF) policy<br>`wafrg` - Web Application Firewall (WAF) policy rule group | `vcn` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | `ne` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer | `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `shared` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter1 |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12 | Instance | `yes` | number | `001` | 

__`gl-vcn-ne-shared-phoebe-infra-prod001`__
__`gl-id-ne-drm-phoebe-sqldb-prod001`__
__`gl-id-ne-drm-phoebe-st-prod001`__
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

Management groups are not following the generic pattern as their structure is strictly defined and won't be changed for a long  period of time. Management group names are strings consisting of lowercase English only characters, numbers and dash could be used as delimiters to enhance readability.

>- htss
>- landing-zones
>- management
>- identity-service

___

#### 3.4.2 Subscriptions

Unlike the general pattern, Subscriptions needs to have different identification (#5 - Billing license enumeration) in it's name that is described and shown in the table below:

_* general [conditions](#user-content-3.1-conditions%3A) are propagated to Subscriptions naming convention_

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Example__ |
|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | `gl` | 
| \#2 | Delimiter |  | 1 dash | `-` |  |
| \#3 | Resource type | `yes` | `sub` - Subscription<br> | `sub` |
| \#4 | Delimiter |  | 1 dash | `-` |  |
| \#5 | Billing license enumerations | `yes` | [2.6 Billing License enumerations](#user-content-2.6-billing-license-enumerations) | `ea` | 
| \#6 | Delimiter |   | 1 dash | `-` |  |
| \#7 | Customer | `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | `drm` | 
| \#8 | Delimiter |   | 1 dash | `-` |  |
| \#9 | Project | `yes` | letters and numbers | `phoebe` | 
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Role, Function or Context name | __`no`__ | letters and numbers | `k8s`<br>`vms`<br>`web`<br>`networking`<br>`databases`<br>`webapps`<br>`infra`<br>`ionut` <br> `...` | An __optional__  context that  identifies or defines some characteristics of the deployment.|
| \#10 | Delimiter |  | 1 dash | `-` |  |
| \#11 | Environment | `yes` | [2.5 Environment enumeration](#user-content-2.5-environment-enumerations) long form | `prod` |
| \#12| Instance | `yes` | number | `001` | 

__`gl-sub-ea-drm-phoebe-infra-prod001`__
__`gl-sub-ea-htss-phoebe-prod001`__
__`cz-sub-csp-drm-phoebe-test001`__
__`gl-sub-mca-ame-phoebe-dev001`__
__`gl-sub-ea-shared-phoebe-prod001`__

___

#### 3.4.3 Virtual Machines

Azure virtual machines have two distinct names: resource name and hostname. When you deploy a virtual machine, the same value is used for both names. The restrictions regarding the name max limit characters are for the host name. The actual resource name can have up to 64 characters (Linux-based VMs) and up to 15 characters (Windows Based VMs). VM names for htss organization will have a  maximum of 15 characters (no matter the base layer OS) for symmetry, management and governance (ADDS, AAD, SCCM, Intune, etc) purposes and we're going to stick to the conditions below.

__Contitions:__
- Only standard English alphanumeric characters
- Strictly lowercase in all main parent resource types
- Can't use spaces, control characters, or these characters:
>- `~ ! @ # $ % ^ & * ( ) = + _ [ ] { } \ | ; : . ' " , < > / ?`
- Length is 15 characters max
- Abbreviations will be consumed from [2.6 VM type enumerations](#user-content-2.6-vm-type-enumerations)
- Each naming order will have a limited number of characters as shown in the example table below

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `ww` - Workstation<br>`ws` - Windows Server<br>`ls` - Linux Server<br>`ss` - Scale Set<br>`us` - Unix Server<br>`wd` - Windows virtual desktop<br>`cn` - Container | 2 | `ls` |
| \#3 | Location | `yes` | [enumeration](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Project short form | `yes` | [2.8 Project enumeration](#user-content-2.8-project-enumerations) | 2 | __`ps`__ |
| \#5 | Project count | `yes` | numeric string | 1 | `1` |
| \#6 | Role, function or context - short form | `yes` | [service/roles enumeration](#user-content-2.9-service/roles-enumerations) | 3 | __`rmq`__ | 
| \#7 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#8| Instance count | `yes` | numeric string | 2 | `01` | 

__`gllsneps1rmqp01`__
__`rowsnesh5cslp02`__
__`czlsnemc1webp01`__
__`plwsnecb2elsd03`__
__`bglsnecb1elsd23`__

___

#### 3.4.4 Storage accounts

Storage account families do not follow generic pattern as they have naming length restrictions imposed by Microsoft. Global scoped Storage Accounts must be 24 characters. Given this condition, we are going to apply the same naming policies for storage resources in the following table.

__Contitions:__
- Only standard English alphanumeric characters
- Strictly lowercase in all resource types
- Can't use spaces, control characters, or these characters:
>- `~ ! @ # $ % ^ & * ( ) = + _ [ ] { } \ | ; : . ' " , < > / ?`
- Length is 24 characters max
- Each naming order will have a limited number of characters as shown in the example table below

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `st` - Storage Account<br>`stdiag` - Storage Account for diagnostic logs<br> `ssimp` -  Azure StorSimple<br> `dla` - Data Lake Analytics<br> `dls` - Data Lake Storage Account<br> `savm` - Virtual Machine Storage account<br>`bvault` - Backup Vault Name<br> `bkpol` - Backup Vault Policy<br>`share` - File Share | 2-6 | `st` |
| \#3 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | 3-4 |  `shr` | 
| \#5 | Project short form | `yes` | [2.8 Project enumeration](#user-content-2.8-project-enumerations) | 2 | __`ps`__ |
| \#6 | Role, Function or Context name | __`no`__ |  string |min: 4<br> max: 9 | `smb`<br>`table`<br>`blobs`<br>`nfs`<br>`logs`<br>`...`
| \#7 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#8| Instance | `yes` | number | 3 | `001` | 

__`glstneshrpsblobsp001`__
__`glstnehtsspsnfsp001`__
__`glstnedrmpssmbp001`__
__`rostnedrmpslogst002`__

___

#### 3.4.5 Key Vaults

Key Vaults are following the same conditions as [Storage Accounts](#user-content-3.4.4-storage-accounts), the resource naming needs to be 24 characters long imposed by Microsoft.

| __Order__ | __Meaning__ | __Required__ | __Format__ | __Characters__| __Example__ |
|--|--|--|--|--|--|
| \#1 | Country Code | `yes` | [2.3 Country Code enumerations - ISO-3166 alpha 2](#user-content-2.3-country-enumerations---iso-3166-alpha-2) | 2 | `gl` | 
| \#2 | (Common) Resource types | `yes` | `kv` - Key Vault | 2 | `kv` |
| \#3 | Location | `yes` | [2.4 Location enumerations](#user-content-2.4-location-enumerations) | 2 | `ne` | 
| \#4 | Customer| `yes` | [2.10 Customer/Client enumerations](#user-content-2.10-customer/client-enumerations) | 3-4 |  `shr` | 
| \#5 | Project short form | `yes` | [2.8 Project enumeration](#user-content-2.8-project-enumerations) | 2 | __`ps`__ |
| \#6 | Role, Function or Context name | __`no`__ |  string |min: 4<br> max: 9 | `secrets`<br>`keys`<br>`certs`<br>`mixed`<br>`star`<br>`...`
| \#7 | Environment | `yes` | [2.5 Environment enumerations](#user-content-2.5-environment-enumerations) short form | 1 | `p` |
| \#8| Instance | `yes` | number | 3 | `001` | 

__`glkvneshrpscertsp001`__
__`glkvnedrmpsstarp001`__
__`glkvnehtssmcmixedp001`__
___

#### 3.4.6 Azure Container Registries

See [__Azure Container Registry__](#excr).

___

#### 3.4.7 Dependent resources

The dependent resources will follow a completely __different pattern__ that will be described more, with examples, in the following chapter.
Parent's resource & Dependent Resource types will be written using __uppercase__ characters. Also, for dependent resources __long form of enumerations will be used by default__.<br>

From the parent name of the resource we will only use the some of the original characteristics as shown in table below with preliminary/unexplained examples:

|[optional]__Role, Function or Context name__|-|__Project__|-|__Environment__|[parent]__Instance Count__|-|__Resource Type__|-|__Dependent Resource Type__|[dependent_resource]__Instance Count__|
|--|--|--|--|--|--|--|--|--|--|--|
|infra|-|phoebe|-|prod|001|-|LB|-|PIP|001|
|webapps|-|phoebe|-|prod|001|-|SQL|-|PEP|001|
|csl|-|phoebe|-|prod|001|-|LS|-|OSDISK|001|

Going deeper into understanding this pattern, we are going to specify naming examples for common resources use cases.

- Virtual Machines - Dependent resources

|__Parent Resource Name__|__osDisk__|__dataDisk__|__networkInterface__|__publicIP__|
|--|--|--|--|--|
|`gllsnemc1cslp01`|`csl-mindclass-prod001-LS-OSDISK001`|`csl-mindclass-prod001-LS-DATADISK001`|`csl-mindclass-prod001-LS-NIC001`|`csl-mindclass-prod001-LS-PIP001`|
|`glwsneps1rmqp01`|`rmq-poseidon-prod001-WS-OSDISK001`|`rmq-poseidon-prod001-WS-DATADISK001`|`rmq-mindclass-prod001-WS-NIC001`|`csl-mindclass-prod001-WS-PIP001`|

_* snapshots will inherit the dependent resource name followed by it's proprietary suffix: `-SNAP001`._
eg: `rmq-poseidon-prod001-WS-DATADISK001-SNAP001`

- Storage Account, Container Registry, Key Vaults - Dependent resources

|__Parent Resource Name__|__privateEndpoint__|
|--|--|
|__Storage Account__|
|`glstneshrpsblobsp001`|`blobs-poseidon-prod001-ST-PEP001`|
|`glstnehtsspsnfsp001`|`nfs-poseidon-prod001-ST-PEP001`|
|__Container Registry__|
|`glcrnedrmphoebek8sprod001`|`k8s-phoebe-prod001-CR-PEP001`
|`glcrwesharedphoebewebappsprod004`|`webapps-phoebe-prod004-CR-PEP001`|
|__Key Vaults__|
|`glkvneshrpscertsp001`|`certs-poseidon-prod001-KV-PEP001`|
|`glkvnehtssmcmixedp001`|`mixed-mindclass-prod001-KV-PEP001`|

- SQL Server, Redis, WebApps - Dependent Resources

|__Parent Resource Name__|__privateEndpoint__|
|--|--|
|__SQL Server__|
|`gl-sql-ne-shared-phoebe-webapps-prod001`|`webapps-phoebe-prod001-SQL-PEP001`|
|`gl-sql-ne-drm-phoebe-infra-test003`|`infra-phoebe-test003-SQL-PEP001`|
|__Redis__|
|`gl-redis-ne-htss-phoebe-web-prod001`|`web-phoebe-prod001-REDIS-PEP001`|
|`cz-redis-ne-drm-phoebe-star-prod001`|`star-phoebe-prod001-REDIS-PEP001`|
|__WebApps__|
|`gl-app-ne-drm-phoebe-php-prod001`|`php-phoebe-prod001-APP-PEP001`|
|`gl-asp-ne-shared-phoebe-nodejs-prod001`|`nodejs-phoebe-prod001-ASP-PEP001`|



__NOTES:__ 
1. If the abbreviation for the dependent resources is present in the official [Azure Abbreviations for resource types](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations) it is mandatory to use it inside generated names. (e.g. - pip, pep, pl, etc)
For instance, DNS Groups that do not have an abbreviation, we can use `-DNSG`. There are also cases in which the abbreviations do not exist so we have the freedom to compose our own and define it in the table below:

|__Resource type__|__Custom abbreviation__|
|--|--|
|DNS Group|`-DNSG001`|
|DNS Configuration|`-DNSCONF001`|
|Virtual Link| `-VLINK001`|
|TBD|

2. For resources that are lacking the Role, Function or Context name, the same pattern will be applied ignoring the missing field.

3. Public IPs resource type can be:
>- standalone - will use the generic pattern; publicIP needs to be reserved in some cases and, for instance, it's association can be changed from NIC to LB
__`gl-pip-ne-htss-phoebe-web-prod001`__

>- dependent - will use the Dependent Resource Pattern

|__Parent Resource Name__|__publicIP__|
|--|--|
|__Load Balancer__|
|`gl-lb-ne-drm-phoebe-infra-prod001`|`infra-phoebe-prod001-LB-PIP001`|
|`ro-lb-ne-htss-phoebe-csl-dev016`|`csl-phoebe-dev016-LB-PIP001`|
___

### 4.0 Tagging strategy

Tags will be applied to __all resources__. Mandatory tags need to be applied to every resource. Optional tags can be added in addition to the mandatory ones, as needed with no restrictions. Tagging strategy for mandatory tags is described in the table below:

|__Tag Key__|__Value Format__|__Example__|__Mandatory__|
|--|--|--|--|
|country| [2.3 Country](#user-content-2.3-country-enumerations---iso-3166-alpha-2) short form|`ro`|yes|
|costCenter|[2.2 Business Unit](#user-content-2.2-business-unit-enumerations) short form|`prd`|yes|
|projectName|string|`Phoebe`|yes|
|projectID|project identificator|`HTSS`|yes|
|environment|[2.4 Environment enumerations](#user-content-2.5-environment-enumerations)|`prod`|yes|
|owner|AAD principal name|`john.doe@htss.ro`|yes|
|projectName|string|`Phoebe`|yes|
|deployment|string|`terraform`<br>`clickops`|yes|
|description|Small project description/scope|`testing terraform for Phoebe`|no|
|role|description of service role|`consul`<br>`elastic`<br>`web server`<br>`rabbitmq`<br>`java framework`<br>`etc`|no|

<br>

____

### 5.0 Summary

In conclusion, the implementation of this comprehensive naming convention logic for Azure provides a solid foundation for organizing and managing resources within our cloud environment. By adhering to these standardized guidelines, we can streamline operations, enhance visibility, and ensure consistent naming practices across our Azure infrastructure. This approach promotes clarity, scalability, and collaboration among teams, empowering us to maximize the benefits of Azure's capabilities while minimizing potential complexities. As we move forward, let us embrace this naming convention as a valuable tool in our pursuit of optimized cloud management and continued success in the ever-evolving digital landscape.

#### 5.1 Generic pattern overview:

|__gl__|-|__sql__|-|__ne__|-|__shared__|-|__phoebe__|-|__webapp__|-|__prod__|__001__|
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
|Country Code|-|Resource type|-|Azure Region|-|Customer|-|Project|-|Context, Role, Function|-|Env type|Instance count|
|Global Serice|-|SQL Server|-|North Europe|-|shared managed service|-|Phoebe Project|-|WebApp connects to it|-|Productive System|Instance 001|


#### 5.2 Limited characters pattern overview:

__VM__
|__gl__|__ls__|__we__|__ps__|1|__csl__|__p__|__001__|
|--|--|--|--|--|--|--|--|
|Global Service|Linux Server|West Europe|Poseidon Project|Project Count|Consul|Production|Instance 001|
|2|2|2|2|1|3|1|3|

__Others__

|__gl__|__st__|__ne__|__drm__|__ps__|__blobs__|__p__|__001__|
|--|--|--|--|--|--|--|--|
|Global Service|Storage Account|North Europe|DrMax Customer|Poseidon Project|blobs|Production|Instance 001|
|2|2-6|2|3-4|2|4-9|1|3|

|__gl__|__kv__|__we__|__shr__|__ps__|__certs__|__p__|__001__|
|--|--|--|--|--|--|--|--|
|Global Service|Key Vault|West Europe|Shared Service|Poseidon Project|hosting Certficates|Production|Instance 001|
|2|2|2|3-4|2|8-9|1|3|

#### 5.3 Dependent Resources pattern overview

|__csl__|-|__phoebe__|-|__prod__|-|__LS__|-|__OSDISK001__|
|--|--|--|--|--|--|--|--|--|
|Context, Role or Function|-|Project|-|Env|-|Parent Resource type|-|Dependent Resource type|
|Consul|-|Project Phoebe|-|Productive system|-|Linux Server|-|disk hosting OS|

|__infra__|-|__phoebe__|-|__prod__|-|__LB__|-|__PIP001__|
|--|--|--|--|--|--|--|--|--|
|Context, Role or Function|-|Project|-|Env|-|Parent Resource type|-|Dependent Resource type|
|Serves infrastructure|-|Project Phoebe|-|Productive Lifecycle|-|Parent is Load Balancer|-|Public IP|

____
<br>
Ta-daaa!

<br>

____