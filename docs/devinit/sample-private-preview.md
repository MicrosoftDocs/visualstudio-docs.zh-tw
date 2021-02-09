---
title: 私用 Beta 版
description: GitHub Codespaces Visual Studio preview Beta 存放庫中使用的自訂範例。
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
ms.openlocfilehash: 93d71449553de3b27916052ef3fd230bde57fdee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932849"
---
# <a name="private-beta"></a>私用 Beta 版

此範例說明如何自訂 Visual Studio 的 codespace，使其具有與初始 [GitHub Codespaces](https://github.com/features/codespaces) 私用搶鮮版相同的功能。

## <a name="devinitjson"></a>.devinit.json

檔案的內容 [`.devinit.json`](devinit-json.md) 。 此檔案必須位於與 _.devcontainer.js_ 的相同資料夾中。

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
