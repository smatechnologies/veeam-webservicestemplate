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
![STEP01_RequestBody](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/img/Step1_02.png)
**Step Completion 200**
