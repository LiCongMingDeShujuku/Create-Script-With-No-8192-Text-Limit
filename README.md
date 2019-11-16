![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 创建没有8192文本限制的脚本
#### Create Script With No 8192 Text Limit
**TIME STAMP**

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
使用‘for xml path(”), type’会允许你创建文本输出而不会遇到8192 Text限制。只需单击XML结果链接，你将获得包含文本结果的第二个选项卡。 要解析的话， 只需将其复制并粘贴到另一个SSMS窗口即可。


## English
Using the ‘for xml path(”), type’ will allow you to create text output without running into the 8192 Text limit. Simply click on the XML results link, and you’ll get a second tab with your text results. To parse; simply copy and paste it into another SSMS window.

---
## Logic
```SQL
use master;
set nocount on
declare @backup_db  varchar(max)
set     @backup_db  = ''
select  @backup_db  = @backup_db + 
'backup database [' + name + '] to disk = ''\\MyBackupShare\MyBackupFolder\' + name + '.bak'' with format;' + char(10)
from sys.databases
where name not in ('tempdb')
order by name asc
select  (@backup_db) for xml path(''), type
-- exec (@backup_db)


```
下面是截图。 （Here’s a quick screenshot.）

![#](images/create-script-with-no-8192-text-limitation.png?raw=true "#")


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

