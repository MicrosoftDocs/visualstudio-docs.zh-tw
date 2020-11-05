---
title: require-nodejs
description: devinit 工具需要-nodejs。
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 6ba6b5a53c6b6f1c67c957c55a612cbe461b108c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400264"
---
# <a name="require-nodejs"></a>require-nodejs

此 `require-nodejs` 工具是用來透過 Node.js 組織所散發的 MSI 來安裝 [Node.js](https://nodejs.org/) 。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                     |
| [**輸入**](#input)                              | 字串 | No       | 要安裝的 Node.JS 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。          |

### <a name="input"></a>輸入

`input`屬性可用來指定 Node.js 版本。 您可以在 [Node.js 下載頁面](https://nodejs.org/en/download/)中找到版本清單。 完整的版本號碼需要主要. 路徑 (例如 14.4.0) 如果有的話，安裝將會失敗。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是 Node.js 的 MSI 安裝程式的直接傳遞。  

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-nodejs` 是安裝最新的 LTS 版本的節點，如 Node.JS [網站](https://nodejs.org/en/download/)中所述。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
