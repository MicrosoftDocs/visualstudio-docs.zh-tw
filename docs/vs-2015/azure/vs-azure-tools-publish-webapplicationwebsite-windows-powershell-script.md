---
title: Publish-webapplicationwebsite （Windows PowerShell 指令碼） |Microsoft Docs
description: 了解如何將 web 專案發佈至 Azure 網站。 如果不存在，此指令碼會建立所需的資源在您的 Azure 訂用帳戶中。
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001979"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell 指令碼)
## <a name="syntax"></a>語法
將 web 專案發佈至 Azure 網站。 如果不存在，指令碼會建立所需的資源在您的 Azure 訂用帳戶中。

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>組態
描述部署的詳細資訊，JSON 組態檔路徑。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 是否為必要項？ |true |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="subscriptionname"></a>訂閱名稱
您想要建立網站的 Azure 訂用帳戶的名稱。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="webdeploypackage"></a>WebDeployPackage
若要發佈至網站的 web 部署套件路徑。 您可以使用 Visual Studio 中的 [發佈 Web] 精靈來建立此套件。 如需詳細資訊，請參閱 <<c0> [ 開始使用 Azure 雲端服務和 ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089)。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
使用者名稱和密碼在 Azure 中的 SQL database。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
如果為 true，列印訊息從指令碼輸出資料流。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 是否為必要項？ |False |
| 位置 |具名 |
| 預設值 |False |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="remarks"></a>備註
如需完整的說明，如何使用指令碼建立的開發和測試環境，請參閱[使用 Windows PowerShell 指令碼發佈至開發和測試環境](vs-azure-tools-publishing-using-powershell-scripts.md)。

JSON 組態檔中指定部署詳細的資料。 它包含您指定當您建立專案，例如名稱和網站的使用者名稱的資訊。 它也包含要佈建的資料庫，如果有的話。 下列程式碼顯示範例 JSON 組態檔：

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

您可以編輯 JSON 組態檔，以變更部署的內容。 [網站] 區段是必要的但資料庫區段是選擇性的。

## <a name="next-steps"></a>後續步驟
如需詳細資訊，請參閱[Publish-webapplicationvm （Windows PowerShell 指令碼）](vs-azure-tools-publish-webapplicationvm.md)

