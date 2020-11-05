---
title: require-nuget
description: devinit 工具需要-nuget。
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
ms.openlocfilehash: f58809465e41b3b1b6020de91fe0ab590ca1c428
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400257"
---
# <a name="require-nuget"></a>require-nuget

`require-nuget`下載 NUGET CLI 並新增至 PATH 變數的工具。 NuGet CLI 提供 NuGet 功能的完整範圍，以安裝、建立、發行和管理套件，而不需要對專案檔進行任何變更。 [在此](/nuget/reference/nuget-exe-cli-reference)閱讀更多有關 NuGet CLI 的資訊。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                |
| [**輸入**](#input)                              | 字串 | No       | 要安裝的 NuGet CLI 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                     |

### <a name="input"></a>輸入

`input`是選擇性屬性，用來指定要安裝的 NUGET CLI 版本。 如果 `input` 省略，則會安裝最新版本的 CLI。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-nuget` 是安裝最新的 NUGET CLI。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file that downloads NuGet CLI and adds to PATH variable.'",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
            "comments": "Installs NuGet for given input version. If no input given, then installs latest."
        }
    ]
}
```