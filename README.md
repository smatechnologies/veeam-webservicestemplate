# VEEAM BACKUP Web Services Connector
This is a template for starting Veeam Agent backup jobs configured in Veeam Backup & Replication.

# Disclaimer
No Support and No Warranty are provided by SMA Technologies for this project and related material. The use of this project's files is on your own risk.

SMA Technologies assumes no liability for damage caused by the usage of any of the files offered here via this Github repository.

# Prerequisites
- OpCon V19.1
- Web Services Connector V 20.0.3 
- Veeam Backup Enterprise Manager  [documentation api](https://helpcenter.veeam.com/docs/backup/rest/overview.html?ver=100)
- Create two new Global Properties : 
  - [[Veeam-url]] : your veeam API url  example https://win2012r2:9398/
  - [[Veeam-Auth]] : Value User:Password (base64 encoded) 

# Instructions
- Download the latest [release](https://github.com/SMATechnologies/veeam-webservicestemplate/releases/tag/V1.0)  of .json file 
- Create your Opcon job Type = Windows, Sub-type = Web Services and import your template see [documentation](https://github.com/SMATechnologies/veeam-webservicestemplate/blob/master/Documentation/Veeam-backup-agent-instructions.docx)
- Change in steps 2 & 3 *idofyourbackupagentjob* in the url address with your job ID. You can use Global Proterties or job instances. 


# License
Copyright 2019 SMA Technologies

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at [apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

# Contributing
We love contributions, please read our [Contribution Guide](CONTRIBUTING.md) to get started!

# Code of Conduct
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](code-of-conduct.md)
SMA Technologies has adopted the [Contributor Covenant](CODE_OF_CONDUCT.md) as its Code of Conduct, and we expect project participants to adhere to it. Please read the [full text](CODE_OF_CONDUCT.md) so that you can understand what actions will and will not be tolerated.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at [apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

# Contributing
We love contributions, please read our [Contribution Guide](CONTRIBUTING.md) to get started!

# Code of Conduct
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](code-of-conduct.md)
SMA Technologies has adopted the [Contributor Covenant](CODE_OF_CONDUCT.md) as its Code of Conduct, and we expect project participants to adhere to it. Please read the [full text](CODE_OF_CONDUCT.md) so that you can understand what actions will and will not be tolerated.


> Written with [StackEdit](https://stackedit.io/).
