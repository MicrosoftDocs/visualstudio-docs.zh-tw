---
title: Node.js 應用程式
description: 範例存放庫，使用 devinit 來安裝適用于 Node.js Express 專案的 npm 套件。
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
ms.openlocfilehash: 0099c6404ef4189732ec5f0729239730815cb190
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943555"
---
# <a name="nodejs-app"></a>Node.js 應用程式

如需使用 devinit 來安裝 Node.js Express 專案之 npm 套件的完整範例，請參閱 [devinit nodejs](https://github.com/microsoft/devinit-example-nodejs) 存放庫。

## <a name="devinitjson"></a>.devinit.json

存放庫根目錄中檔案 _.devinit.js_ 的內容。

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the body-parser package.",
      "tool": "npm-install",
      "input": "body-parser"
    },
    {
      "comments": "Installs the cookie-parser package.",
      "tool": "npm-install",
      "input": "cookier-parser"
    },
    {
      "comments": "Installs the debug package.",
      "tool": "npm-install",
      "input": "debug"
    },
    {
      "comments": "Installs the express package.",
      "tool": "npm-install",
      "input": "express"
    },
    {
      "comments": "Installs the morgan package.",
      "tool": "npm-install",
      "input": "morgan"
    },
    {
      "comments": "Installs the pug package.",
      "tool": "npm-install",
      "input": "pug"
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
