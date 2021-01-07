### Instruction step by step 
Here we use the agentBackup option, you can easily find further options in the [Veeam RESTful API Reference documentation](https://helpcenter.veeam.com/docs/backup/rest/overview.html?ver=100).

##Step 1

#Create a new logon session

POST [[veeam-url]]/api/sessionMngr/?v=v1_5  

**Request Header**: Authorization: Basic [[Veeam-Auth]]  

![STEP01_RequestHeader](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Img/Step1_01.png)
