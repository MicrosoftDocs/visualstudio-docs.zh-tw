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
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943582"
---
# <a name="net-core-app"></a>.NET Core 應用程式

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
