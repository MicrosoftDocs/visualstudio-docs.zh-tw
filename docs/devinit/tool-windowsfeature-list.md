---
title: windowsfeature-list
description: devinit 工具的，清單。
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
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400195"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

此 `windowsfeature-list` 工具可用來列出所有 Windows 功能的啟用/停用狀態。

| 名稱                                             | 類型   | 必要 | 值                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。      |
| [**輸入**](#input)                              | 字串 | No       | 未使用。 忽略。                         |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 忽略。                         |

### <a name="input"></a>輸入

未使用。 忽略。

#### <a name="additional-options"></a>其他選項

未使用。 忽略。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `windowsfeature-list` 是列出所有 Windows 功能的啟用/停用狀態。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
