---
title: .NET Core 執行階段
description: 針對 dotnet/執行時間存放庫使用 devinit 進行自訂的範例。
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
ms.openlocfilehash: 477a498059be6d1ee5637a704512fd49b62e11b6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809108"
---
# <a name="net-core-runtime"></a>.NET Core 執行階段

此範例說明如何自訂 .NET Core 執行時間 [dotnet/運行](https://github.com/dotnet/runtime) 時間，以使用 [GitHub Codespaces](https://github.com/features/codespaces)自動布建。

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

此腳本是從 _PostCloneSetup.ps1_ 呼叫，也可以在本機執行以設定存放庫。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```batch
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_檔案是[Chocolatey](https://chocolatey.org/)檔案，可定義要安裝的 Chocolatey 封裝清單。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.js開啟

檔案 [_.devinit.js_](devinit-json.md) 的內容。 這個檔案必須與檔案 _.devcontainer.js_ 位於相同的資料夾中。

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
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
