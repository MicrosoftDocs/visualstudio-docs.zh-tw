---
title: .NET Core 應用程式
description: 使用 devinit 安裝特定 .NET Core SDK 的範例存放庫。
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028142"
---
# <a name="net-core-app"></a>.NET Core 應用程式

如需使用 devinit 在 Codespaces 中安裝必要 .NET Core SDK 版本的完整範例，請參閱 [DevinitExample](https://github.com/microsoft/DevinitExample) 存放庫。

## <a name="devinitjson"></a>.devinit.json

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