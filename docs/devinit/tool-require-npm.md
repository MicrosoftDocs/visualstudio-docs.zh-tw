---
title: 需要-npm
description: devinit 工具需要-npm。
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
ms.openlocfilehash: 56c8bc0d277427d235396671f446a44125aa0165
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809676"
---
# <a name="require-npm"></a>需要-npm

此 `require-npm` 工具是用來安裝 [NPM](https://www.npmjs.com/)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                       |
| [**輸入**](#input)                              | 字串 | 是      | 指定 NPM 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。                           |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                  |

### <a name="input"></a>輸入

`input`屬性是用來指定 NPM 版本。

### <a name="additional-options"></a>其他選項

未使用的。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-nodejs` 是安裝最新的 LTS 版本的 NPM。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of NPM.",
            "tool": "require-npm"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```
