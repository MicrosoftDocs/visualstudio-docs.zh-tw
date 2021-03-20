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
ms.openlocfilehash: 3225e67db734e02abce96820d44ca1515ddc348f
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672628"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

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
