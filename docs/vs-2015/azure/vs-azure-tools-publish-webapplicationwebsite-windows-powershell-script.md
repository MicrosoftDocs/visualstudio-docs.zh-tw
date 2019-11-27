---
title: Publish-WebApplicationWebSite (Windows PowerShell 指令碼) | Microsoft Docs
description: 了解如何將 Web 專案發佈至 Azure 網站。 此指令碼會在您的 Azure 訂用帳戶中建立所需的資源 (如果它們不存在)。
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 6c9c2e281ace3b483d1f37552fba0cc6f490978a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298130"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell 指令碼)
## <a name="syntax"></a>語法
將 Web 專案發佈至 Azure 網站。 指令碼會在您的 Azure 訂用帳戶中建立所需的資源 (如果它們不存在)。

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>設定
描述部署詳細資訊的 JSON 組態檔路徑。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 必要？ |true |
| 位置 |已命名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="subscriptionname"></a>SubscriptionName
您要建立網站的 Azure 訂用帳戶名稱。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 必要？ |False |
| 位置 |已命名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="webdeploypackage"></a>WebDeployPackage
要發佈至網站的 Web 部署封裝路徑。 您可以使用 Visual Studio 的 [發佈 Web] 精靈來建立此封裝。 如需詳細資訊，請參閱 [開始使用 Azure 雲端服務和 ASP.NET](https://go.microsoft.com/fwlink/p/?LinkID=623089)。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 必要？ |False |
| 位置 |已命名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
在 Azure 中 SQL Database 的使用者名稱和密碼。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 必要？ |False |
| 位置 |已命名 |
| 預設值 |無 |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
如果為 true，將訊息從指令碼列印至輸出資料流。

| 參數 | 預設值 |
| --- | --- |
| 別名 |無 |
| 必要？ |False |
| 位置 |已命名 |
| 預設值 |False |
| 接受管線輸入？ |False |
| 接受萬用字元？ |False |

## <a name="remarks"></a>備註
如需如何使用指令碼來建立開發和測試環境的完整說明，請參閱 [使用 Windows PowerShell 指令碼來發佈至開發和測試環境](vs-azure-tools-publishing-using-powershell-scripts.md)。

JSON 組態檔會指定待部署項目的詳細資料。 它會包含您在建立專案時所指定的資訊，例如網站的名稱和使用者名稱。 它還包含要佈建的資料庫 (如果有的話)。 下列程式碼片段將顯示一個 JSON 組態檔範例：

```json
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
```

您可以編輯 JSON 組態檔來變更部署項目。 webSite 是必要區段，database 是選擇性區段。

## <a name="next-steps"></a>後續步驟
如需詳細資訊，請參閱 [Publish-WebApplicationVM (Windows PowerShell 指令碼)](vs-azure-tools-publish-webapplicationvm.md)
