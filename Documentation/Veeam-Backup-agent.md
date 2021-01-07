# Instruction step by step #
Here we use the agentBackup option, you can easily find further options in the [Veeam RESTful API Reference documentation](https://helpcenter.veeam.com/docs/backup/rest/overview.html?ver=100).

Create your Opcon job Type = Windows, Sub-type = Web Services and import your template  

## Variable ##  
In the GLOBAL VALUE tab create a variable @BackupAgentJobId with your job id as value  
  
  
![Variable Tabs](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/variable_01.PNG)
  
  
## Step 1 ##  

### Create a new logon session ###  

POST [[veeam-url]]/api/sessionMngr/?v=v1_5  

**Request Header**: Authorization: Basic [[Veeam-Auth]]  
  
  
![STEP01_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step1_01.png)  


**Message Body**  
{"id":null}  

![STEP01_RequestBody](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step01_02.png)  
  
  

If logon was successful, the server returns the created authentication token in the X-RestSvcSessionId header of the response. The client must obtain the returned authentication token and add it to the header of every subsequent request to the server.  

**Response Header:** X-RestSvcSessionId *(use it in each step)*  

**Example :** X-RestSvcSessionId: NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  

**Response Body:**  
@hrefls = link to delete logonSessions *(use it in step7)*  
  
  
![STEP01_Response](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step01_03.png)  
  
  
**Step Completion 201**  

## STEP 2 ##  
### Represents a Veeam Agent backup job having the specified ID. The Veeam Agent backup job is configured in Veeam Backup & Replication ###  
GET [[veeam-url]]api/agents/jobs/@BackupAgentJobId?format=Entity  
**Request Header:** X-RestSvcSessionId  
![STEP02_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step02_01.PNG)  
**Message Body**  
{"id":null}  
![STEP02_RequestBody](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step02_02.PNG)  
**Step Completion 200**  

## STEP 3 ##  
### Start job ###  
The job is started asynchronously: Veeam Backup Enterprise Manager creates a new task for the job start and returns 202 ACCEPTED status to the client. In the response body, Veeam Backup Enterprise Manager returns a resource representation of the task.  
POST [[veeam-url]]api/agents/jobs/@BackupAgentJobId?action=start  
**Request Header:** X-RestSvcSessionId  
![STEP03_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step03_01.PNG)  
**Message Body**  
{"id":null}  
![STEP03_RequestBody](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step03_02.PNG)  
**Response Body:**  
@idtask = TaskId Id of the task *(use it in step 4 & 5)* 
![STEP03_Response](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step03_03.PNG)  
**Step Completion 202**  

## STEP 4 ##  
### Trace the task performance and check the task result ###  
GET [[veeam-url]]/api/tasks/@idtask  
**Request Header:** X-RestSvcSessionId  
![STEP04_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step04_01.PNG)  
Check returned Data  
![STEP04_ReturnedData](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step04_02.PNG)  
**Step Completion 200**  

## STEP 5 ## 
### Retrieve the backupSession number ###  
Send the same request as in step 4 and retrieve the value of the BackupSession link  
GET [[veeam-url]]/api/tasks/@idtask  
**Request Header:** X-RestSvcSessionId  
![STEP05_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step05_01.PNG)  
**Reponse body:** Link of backupSession *(use it in step 6)*  
![STEP05_Response](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step05_02.PNG)  
**Step Completion 200**  

## STEP 6 ##  
### Retrieve the status of backupSession ###  
GET @hrefbs  
**Example :** GET https://win2012r2:9398/api/agents/backupSessions/e7888ea7-2f96-4668-bf10-dbfe18a2d846?format=Entity  
**Request Header:** X-RestSvcSessionId  
![STEP06_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step06_01.PNG)  
Check returned Data  
![STEP06_ReturnedData](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step06_02.PNG)  
**Step Completion 200**  

## STEP 7 ##  
### Logout Session ###  
Delete @hrefls  
**Example :** DELETE https://win2012r2:9398/api/logonSessions/85b332b4-7276-4b78-abd7-9e96491505e7  
**Request Header:** X-RestSvcSessionId  
![STEP07_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step07_01.PNG)  
**Step Completion 204**  
