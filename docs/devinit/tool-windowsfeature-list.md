---
title: windowsfeature-list
description: devinit 工具的，清單。
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 43370389aaffdb4395248fed6ec83de39f16c86d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874502"
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
