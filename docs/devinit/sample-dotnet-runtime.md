---
title: .NET Core 執行階段
description: 針對 dotnet/執行時間存放庫使用 devinit 進行自訂的範例。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: d703e71b6f8ab57ab07c4143fdd5435585c6004c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672450"
---
# <a name="net-core-runtime"></a>.NET Core 執行階段

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此範例說明如何自訂 .NET Core 執行時間 [dotnet/運行](https://github.com/dotnet/runtime) 時間，以使用 [GitHub Codespaces](https://github.com/features/codespaces)自動布建。

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

此腳本是從 _PostCloneSetup.ps1_ 呼叫，也可以在本機執行以設定存放庫。 此檔案必須位於與 _.devcontainer.js_ 的相同資料夾中。

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_ 檔案是 [Chocolatey](https://chocolatey.org/)檔案，可定義要安裝的 Chocolatey 封裝清單。 此檔案必須位於與 _.devcontainer.js_ 的相同資料夾中。

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

檔案的內容 [`.devinit.json`](devinit-json.md) 。 這個檔案必須與檔案 _.devcontainer.js_ 位於相同的資料夾中。

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
