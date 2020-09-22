---
title: eShopOnWeb
description: 針對 dotnet 架構/eShopOnWeb 存放庫使用 devinit 進行自訂的範例。
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 052e89d276e122ebf44c2b541771bbb314f48ade
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809101"
---
# <a name="eshoponweb"></a>eShopOnWeb

此範例說明如何自訂 dotnet 架構範例 [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) ，以使用 [GitHub Codespaces](https://github.com/features/codespaces)來自動布建。

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

此腳本是從 _PostCloneSetup.ps1_ 呼叫，也可以在本機執行以設定存放庫。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```batch
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.js開啟

檔案 [_.devinit.js_](devinit-json.md) 的內容。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js開啟

存放庫根目錄中檔案 _.devcontainer.js_ 的內容。

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
