---
title: windowsfeature-list
description: devinit 工具的，清單。
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 07b92e8783393fa19e5c09344a396a6c5c4fc011
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442123"
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
以下是如何使用執行的範例 `windowsfeature-list` `.devinit.json` 。

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.js，將會列出所有 Windows 功能的狀態：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
