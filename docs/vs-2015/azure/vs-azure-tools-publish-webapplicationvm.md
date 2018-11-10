---
title: Publish-webapplicationvm |Microsoft Docs
description: 了解如何部署虛擬機器的 web 應用程式。 如果不存在，此指令碼會建立所需的資源在您的 Azure 訂用帳戶中。
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002045"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell 指令碼)
Web 應用程式部署到虛擬機器。 如果不存在，指令碼會建立所需的資源在您的 Azure 訂用帳戶中。

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>組態
描述部署的詳細資訊，JSON 組態檔路徑。

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |true |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="subscriptionname"></a>訂閱名稱
您要建立虛擬機器的 Azure 訂用帳戶的名稱。

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |使用訂用帳戶檔案中的第一個訂用帳戶 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="webdeploypackage"></a>WebDeployPackage
若要將發佈至虛擬機器的 web 部署套件路徑。 您可以使用 Visual Studio 中的 [發佈 Web] 精靈來建立此套件。 請參閱[如何： 在 Visual Studio 中建立 Web 部署套件](https://msdn.microsoft.com/library/dd465323.aspx)。

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="allowuntrusted"></a>AllowUntrusted
如果為 true，允許使用不受信任的根授權單位所簽署的憑證。

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |False |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="vmpassword"></a>VMPassword
虛擬機器帳戶的認證。 範例:-VMPassword @{名稱 ="admin";密碼 ="password"}

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
在 Azure 中的 SQL 資料庫認證。 範例:-DatabaseServerPassword @{名稱 ="admin";密碼 ="password"}

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
如果為 true，列印訊息從指令碼輸出資料流。

| 別名 | 無 |
| --- | --- |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |False |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="remarks"></a>備註
如需完整的說明，如何使用指令碼建立的開發和測試環境，請參閱[使用 Windows PowerShell 指令碼發佈至開發和測試環境](vs-azure-tools-publishing-using-powershell-scripts.md)。

JSON 組態檔中指定部署詳細的資料。 它包含您指定當您在建立專案，例如名稱、 同質群組、 VHD 映像和虛擬機器大小的資訊。 它也包含虛擬機器，以佈建時，資料庫上的端點，如果有的話，和 web 部署參數。 下列程式碼顯示範例 JSON 組態檔：

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

您可以編輯 JSON 組態檔，來變更 什麼佈建。 虛擬機器和雲端服務是必要的但資料庫區段是選擇性的。

