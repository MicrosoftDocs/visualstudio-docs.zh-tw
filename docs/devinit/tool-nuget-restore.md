---
title: nuget-restore
description: devinit 工具 nuget-還原。
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
ms.openlocfilehash: 8e525451ffcd691b0dab1260584946ad3d0a561c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440365"
---
# <a name="nuget-restore"></a>nuget-restore

此 `nuget-restore` 工具會還原專案檔中所指定的相依性和專案特有工具。 請 [在這裡](/nuget/reference/cli-reference/cli-ref-restore)閱讀 NuGet 還原的詳細資訊。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                |
| [**輸入**](#input)                              | 字串 | No       | 要還原之專案/方案檔的路徑。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                     |

### <a name="input"></a>輸入

要還原之專案/方案檔的路徑。

### <a name="additional-options"></a>其他選項

其他選項會依原樣傳遞至 NuGet 還原命令。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `nuget-restore` 是 `NuGet restore` 在目前的目錄中執行。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `nuget-restore` `.devinit.json` 。

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.js將會還原專案的相依性和工具：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```