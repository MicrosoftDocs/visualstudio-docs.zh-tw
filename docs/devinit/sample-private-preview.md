---
title: 私人預覽
description: GitHub Codespaces Visual Studio preview Beta 存放庫中使用的自訂範例。
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
ms.openlocfilehash: c240cee6595f060c5347cafc4379a7fc27c8d310
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809087"
---
# <a name="private-preview"></a>個人預覽版

此範例說明如何自訂 Visual Studio 的 codespace，使其具有與初始 [GitHub Codespaces](https://github.com/features/codespaces) 私用搶鮮版相同的功能。

## <a name="devinitjson"></a>.devinit.js開啟

檔案 [_.devinit.js_](devinit-json.md) 的內容。 此檔案必須位於與 _.devcontainer.js_的相同資料夾中。

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
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
