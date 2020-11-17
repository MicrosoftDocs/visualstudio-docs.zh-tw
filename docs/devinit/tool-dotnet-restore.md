---
title: dotnet-restore
description: devinit tool dotnet-restore。
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
ms.openlocfilehash: 51c6ed6576fefe3853bca7f4250c1884bd364f64
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671930"
---
# <a name="dotnet-restore"></a>dotnet-restore

此 `dotnet-restore` 工具會還原專案檔中所指定的相依性和專案特有工具。 如需詳細資訊，請參閱 [此處](/dotnet/core/tools/dotnet-restore)的 dotnet restore。

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

其他選項會依原樣傳遞到 dotnet restore 命令。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `dotnet-restore` 是在目前的目錄中執行 ' dotnet restore '。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `dotnet-restore` `.devinit.json` 。 

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.js將會還原專案的相依性和工具：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```