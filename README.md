#### Q86. You use Azure Table storage to store customer information for an application. The data contains customer details and is partitioned by last name. You need to
create a query that returns all customers with the last name Smith. Which code segment should you use?

- [ ] TableQuery.GenerateFilterCondition("PartitionKey", Equals, "Smith")
- [ ] TableQuery.GenerateFilterCondition("LastName", Equals, "Smith")
- [X] TableQuery.GenerateFilterCondition("PartitionKey", QueryComparisons.Equal, "Smith")
- [ ] TableQuery.GenerateFilterCondition("LastName", QueryComparisons.Equal, "Smith")

Explanation:
Retrieve all entities in a partition. The following code example specifies a filter for entities where 'Smith' is the partition key. This example prints the fields of each
entity in the query results to the console.
Construct the query operation for all customer entities where PartitionKey="Smith". TableQuery<CustomerEntity> query = new
TableQuery<CustomerEntity>().Where(TableQuery.GenerateFilterCondition("PartitionKey",
QueryComparisons.Equal, "Smith"));

[Ref](https://docs.microsoft.com/en-us/azure/cosmos-db/table-storage-how-to-use-dotnet)




#### Q87.You develop an app that allows users to upload photos and videos to Azure storage. The app uses a storage REST API call to upload the media to a blob storage
account named Account1. You have blob storage containers named Container1 and Container2. Uploading of videos occurs on an irregular basis.
You need to copy specific blobs from Container1 to Container2 in real time when specific requirements are met, excluding backup blob copies.
What should you do?



- [ ] Download the blob to a virtual machine and then upload the blob to Container2.
- [X] Run the Azure PowerShell command Start-AzureStorageBlobCopy
- [ ]  Copy blobs to Container2 by using the Put Blob operation of the Blob Service REST API.
- [ ]  Use AzCopy with the Snapshot switch blobs to Container2.

Explanation:
The Start-AzureStorageBlobCopy cmdlet starts to copy a blob. Example 1: Copy a named blob
C:\PS>Start-AzureStorageBlobCopy -SrcBlob "ContosoPlanning2015" -DestContainer "ContosoArchives"
-SrcContainer "ContosoUploads"
This command starts the copy operation of the blob named ContosoPlanning2015 from the container named ContosoUploads to the container named
ContosoArchives.



[Ref](https://docs.microsoft.com/en-us/powershell/module/azure.storage/start-azurestorageblobcopy?view=azurermps)


#### Q88. (Exam Topic 3)
You are a developer for a SaaS company that offers many web services. All web services for the company must meet the following requirements:
Use API Management to access the services Use OpenID Connect for authentication Prevent anonymous usage A recent security audit found that several web services can be called without any authentication.
Which API Management policy should you implement?



- [ ] jsonp
- [ ] authentication-certificate
- [ ] check-header
- [X] validate-jwt

[Ref](https://docs.microsoft.com/en-us/azure/api-management/api-management-howto-protect-backend-with-aad)


#### Q89.You are developing an Azure Cosmos DB solution by using the Azure Cosmos DB SQL API. The data includes millions of documents. Each document may
contain hundreds of properties. The properties of the documents do not contain distinct values for partitioning. Azure Cosmos DB must scale individual containers in the database to meet the
performance needs of the application by spreading the workload evenly across all partitions over time.
You need to select a partition key.
Which two partition keys can you use? Each correct answer presents a complete solution. 
NOTE: Each correct selection is worth one point.



- [X] a concatenation of multiple property values with a random suffix appended
- [ ] a single property value that does not appear frequently in the documents
- [X] a hash suffix appended to a property value
- [ ] a value containing the collection name
- [ ] a single property value that appears frequently in the documents

Explanation:
You can form a partition key by concatenating multiple property values into a single artificial partitionKey property. These keys are referred to as synthetic keys.
Another possible strategy to distribute the workload more evenly is to append a random number at the end of the partition key value. When you distribute items in
this way, you can perform parallel write operations across partitions.
Note: It's the best practice to have a partition key with many distinct values, such as hundreds or thousands. The goal is to distribute your data and workload
evenly across the items associated with these partition key values. If such a property doesn’t exist in your data, you can construct a synthetic partition key.

[Ref](https://docs.microsoft.com/en-us/azure/cosmos-db/synthetic-partition-keys)


#### Q90.You are developing an ASP.NET Core Web API web service. The web service uses Azure Application Insights for all telemetry and dependency tracking. The web
service reads and writes data to a database other than Microsoft SQL Server.
You need to ensure that dependency tracking works for calls to the third-party database.
Which two Dependency Telemetry properties should you store in the database? Each correct answer presents part of the solution.
NOTE: Each correct selection is worth one point.



- [X] Telemetry.Context.Operation.Id
- [ ] Tetemetry.Context.Cloud.Rolelnstance
- [X] Telemetry.Id
- [ ] Telemetry.ContextSession.Id

[Ref](https://docs.microsoft.com/en-us/azure/azure-monitor/app/custom-operations-tracking)


#### Q91. You are preparing to deploy an ASP.NET Core website to an Azure Web App from a GitHub repository. The website includes static content generated by a script.
You plan to use the Azure Web App continuous deployment feature.
You need to run the static generation script before the website starts serving traffic.
What are two possible ways to achieve this goal? Each correct answer presents a complete solution. NOTE: Each correct selection is worth one point



- [ ]  Create a file named .deployment in the root of the repository that calls a script which generates the static content and deploys the website
- [ ]  Add a PreBuild target in the websites csproj project file that runs the static content generation script
- [ ] Create a file named run.cmd in the folder /run that calls a script which generates the static content and deploys the website.
- [ ] Add the path to the static content generation tool to WEBSITE_RUN_FROM_PACKAGE setting in the host.json file.

Explanation:
A: To customize your deployment, include a .deployment file in the repository root.
You just need to add a file to the root of your repository with the name .deployment and the content: [config]
command = YOUR COMMAND TO RUN FOR DEPLOYMENT
this command can be just running a script (batch file) that has all that is required for your deployment, like copying files from the repository to the web root directory
for example.
D: In Azure, you can run your functions directly from a deployment package file in your function app. The other option is to deploy your files in the
d:\home\site\wwwroot directory of your function app (see A above).
To enable your function app to run from a package, you just add a WEBSITE_RUN_FROM_PACKAGE setting to your function app settings.
Note: The host.json metadata file contains global configuration options that affect all functions for a function app.

[Ref](https://github.com/projectkudu/kudu/wiki/Custom-Deployment-Script)
[Ref](https://docs.microsoft.com/bs-latn-ba/azure/azure-functions/run-functions-from-deployment-package)




#### Q92. You provide an Azure API Management managed web service lo clients. The back end web service implements HTTP Strict Transport Security (HSTS).
Every request to the backend service must include a valid HTTP authorization header. You need to configure the Azure API Management instance with an
authentication policy. Which two policies can you uses? Each correct answer presents a complete solution NOTE: Each correct selection is worth one point.


- [X] Certificate Authentication
- [ ] Basic Authentication
- [X] OAuth Client Credential Grant
- [ ] Digest Authentication

#### Q93.A company is implementing a publish-subscribe (Pub/Sub) messaging component by using Azure Service Bus. You are developing the first subscription
application.
In the Azure portal you see that messages are being sent to the subscription for each topic. You create and initialize a subscription client object by supplying the
correct details, but the subscription application is still not consuming the messages.
You need to complete the source code of the subscription client What should you do



- [ ] await subscriptionClient.CloseAsync();
- [ ] await subscriptionClient.AddRuleAsync(new RuleDescription(RuleDescription.DefaultRuleName, new TrueFilter()));
- [x] subscriptionClient.RegisterMessageHandler(ProcessMessagesAsync, messageHandlerOptions);
- [ ] subscriptionClient = new SubscriptionClient(ServiceBusConnectionString, TopicName, SubscriptionName);

Explanation:
Using topic client, call RegisterMessageHandler which is used to receive messages continuously from the entity. It registers a message handler and begins a new
thread to receive messages. This handler is waited on every time a new message is received by the receiver.
subscriptionClient.RegisterMessageHandler(ReceiveMessagesAsync, messageHandlerOptions);


[Ref](https://www.c-sharpcorner.com/article/azure-service-bus-topic-and-subscription-pub-sub/)



#### Q94. You develop a gateway solution for a public facing news API. The news API back end is implemented as a RESTful service and uses an OpenAPI specification.
You need to ensure that you can access the news API by using an Azure API Management service instance. Which Azure PowerShell command should you run?



- [ ] Import-AzureRmApiManagementApi –Context $ApiMgmtContext –SpecificationFormat "Swagger" -SpecificationPath $SwaggerPath –Path $Path
- [ ] New-AzureRmApiManagementBackend -Context $ApiMgmtContext -Url $Url -Protocol http
- [ ] New-AzureRmApiManagement –ResourceGroupName $ResourceGroup –Name $Name – Location $Location –Organization $Org –AdminEmail $AdminEmail
- [x]  New-AzureRmApiManagementBackendProxy –Url $ApiUrl

Explanation:
New-AzureRmApiManagementBackendProxy creates a new Backend Proxy Object which can be piped when creating a new Backend entity.
Example: Create a Backend Proxy In-Memory Object
PS C:\>$secpassword = ConvertTo-SecureString "PlainTextPassword" -AsPlainText -Force
PS C:\>$proxyCreds = New-Object System.Management.Automation.PSCredential ("foo", $secpassword) PS C:\>$credential = NewAzureRmApiManagementBackendProxy 
-ProxyCredential $proxyCred
PS C:\>$apimContext = New-AzureRmApiManagementContext -ResourceGroupName "Api-Default-WestUS" -ServiceName "contoso"
PS C:\>$backend = New-AzureRmApiManagementBackend -Context $apimContext -BackendId 123 Protocol http -Title
"first backend" -SkipCertificateChainValidation $true
-Proxy $credential -Description "backend with proxy server"
Creates a Backend Proxy Object and sets up Backend

#### Q95. You are developing a mobile instant messaging app for a company. The mobile app must meet the following requirements:
• Support offline data sync.
• Update the latest messages during normal sync cycles. You need to implement Offline Data Sync.
Which two actions should you perform? Each conn I answer presents part of the solution. NOTE: Each correct selection is worth one point.


- [ ] Retrieve records from Offline Data Sync on every call to the PullAsync method.
- [x] Retrieve records from Offline Data Sync using an Incremental Sync.
- [ ] Push records to Offline Data Sync using an Incremental Sync.
- [ ] . Return the updatedAt column from the Mobile Service Backend and implement sorting by using the column.
- [X] Return the updatedAt column from the Mobile Service Backend and implement sorting by the message id.

[Ref](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-offline-data-sync)



#### Q96.You develop a website. You plan to host the website in Azure. You expect the website to experience high traffic volumes after it is published. You must ensure tha the website remains available and responsive while minimizing cost. You need to deploy the website. What should you do?


- [ ] Deploy the website to an App Service that uses the Shared service tie
- [ ] Configure the App Service plan to automatically scale when the CPU load is high.
- [X]  Deploy the website to a virtual machin
- [ ] . Configure the virtual machine to automatically scale when the CPU load is high.

Explanation:
Windows Azure Web Sites (WAWS) offers 3 modes: Standard, Free, and Shared.
Standard mode carries an enterprise-grade SLA (Service Level Agreement) of 99.9% monthly, even for sites with just one instance.
Standard mode runs on dedicated instances, making it different from the other ways to buy Windows Azure Web Sites.

#### Q97. You develop a serverless application using several Azure Functions. These functions connect to data from within the code.
You want to configure tracing for an Azure Function App project. You need to change configuration settings in the hostjson file. Which tool should you use?

- [X] Azure porta
- [ ] Azure PowerShell
- [ ] Azure Functions Core Tools (Azure CLI)
- [ ] Visual Studio

Explanation:
The function editor built into the Azure portal lets you update the function.json file and the code file for a function. The host.json file, which contains some runtimespecific configurations, is in the root folder of the function app

[Ref](https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference#fileupdate)



#### Q98. You are developing an internal website for employees to view sensitive data. The website uses Azure Active Directory (AAD) for authentication. You need to
implement multifactor authentication for the website.
What should you do? Each correct answer presents part of the solution. NOTE; Each correct selection is worth one point



- [X] In Azure AD, create a new conditional access policy.
- [ ] In Azure AD, enable application proxy.
- [ ]  Configure the website to use Azure AD B2C.
- [ ] In Azure AD conditional access, enable the baseline policy.
- [X] Upgrade to Azure AD Premium.


[Ref](https://docs.microsoft.com/en-us/azure/active-directory/authentication/howto-mfa-getstarted)



#### Q99. You must implement Application Insights instrumentation capabilities utilizing the Azure Mobile Apps SDK to provide meaningful analysis of user interactions with a
mobile app. You need to capture the data required to implement the Usage Analytics feature of Application Insights. Which three data values should you capture? Each correct
answer presents part of the solution
NOTE: Each correct selection is worth one point.



- [X]  Trace
- [ ]  Session Id
- [ ]  Exception
- [X]  User Id
- [X] Events

Explanation:
Application Insights is a service for monitoring the performance and usage of your apps. This module allows you to send telemetry of various kinds (events, traces,
etc.) to the Application Insights service where your data can be visualized in the Azure Portal. Application Insights manages the ID of a session for you.


[Ref](https://github.com/microsoft/ApplicationInsights-Android)



#### Q100. You develop Azure solutions.
You must connect to a No-SQL globally-distributed database by using the .NET API. You need to create an object to configure and execute requests in the
database. Which code segment should you use?


- [ ] new Container(EndpointUri, PrimaryKey)
- [ ] new Database(Endpoint, PrimaryKey);
- [x] new CosmosClient(EndpointUri, PrimaryKey);


Explanation:
Example:
// Create a new instance of the Cosmos Client
this.cosmosClient = new CosmosClient(EndpointUri, PrimaryKey)
//ADD THIS PART TO YOUR CODE
await this.CreateDatabaseAsync(); 

[Ref](https://docs.microsoft.com/en-us/azure/cosmos-db/sql-api-get-started)
