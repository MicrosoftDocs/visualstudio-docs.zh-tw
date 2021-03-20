---
title: .NET Core 應用程式
description: 使用 devinit 安裝特定 .NET Core SDK 的範例存放庫。
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b3e25835f305a96b2205fc96cc0200d68ad033af
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672457"
---
# <a name="net-core-app"></a>.NET Core 應用程式

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

如需使用 devinit 在 Codespaces 中安裝所需 .NET Core SDK 版本的完整範例，請參閱 [devinit-dotnet 核心](https://github.com/microsoft/devinit-example-dotnet-core) 存放庫。

## <a name="devinitjson"></a>.devinit.json

存放庫根目錄中檔案 _.devinit.js_ 的內容。

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js開啟

存放庫根目錄中檔案 _.devcontainer.js_ 的內容。

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

存放庫根目錄中檔案 _global.js_ 的內容。

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
