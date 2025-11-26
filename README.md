> **Note** — The folder `linguist-samples/` contains tiny real files so GitHub can correctly display all languages used in this repo.  
> The actual content and examples remain in this README.

![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        


# Find SQL Ports With Powershell
**Post Date: November 7, 2016**        



## Contents    
- [About Process](##About-Process)  
- [Powershell Logic](#Powershell-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Ok; so you're looking at another database server, and you want to make sure all the ports are properly configured. You might have the impulse to login to the server, and check the ports out from there, but at this stage you might find logging into the server is a bit annoying if you can just run something locally. Powershell to the rescue.
If you're running Server 2012 or later; all the Powershell cmdlets are already there; you just need to know what to run. Take this little statement. Using PSSESSION you can connect remotely to the server, and get all the "SQL" port information.
The powershell logic to do that is here:</p>      



## Powershell-Logic
```Powershell
enter-pssession "MyServerName"
 
Get-NetFirewallRule `
 
| Where { $_.Enabled -eq 'True' -and $_.Direction -eq 'Inbound' -and $_.'displayname' -like "*sql*" } `
 
| select displayname, enabled, action, direction `
 
| out-string -width 98
 
exit-pssession
```
 




[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)


## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

 
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")
