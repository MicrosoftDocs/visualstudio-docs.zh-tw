---
title: dotnet-toolinstall
description: devinit tool dotnet-toolinstall。
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
ms.openlocfilehash: f6946afa0138dc27a61f5665a9172c231392acc1
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862245"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

此 `dotnet-toolinstall` 工具是用來透過命令安裝 [.Net Core 工具](https://dotnet.microsoft.com/) `dotnet tool update` 。

## <a name="usage"></a>使用量

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                 |
| [**輸入**](#input)                              | 字串 | 是      | 要安裝的 .NET Core 工具。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。      |

### <a name="input"></a>輸入

`input`屬性可用來指定要安裝的 .Net Core 工具。 中有一份非官方的工具清單 [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) 。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是命令所使用之引數的直接傳遞 [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) 。 

此 `dotnet tool update` 命令可用來安全地處理已安裝工具的情況。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `dotnet-toolinstall` 是在需要時發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install the dotnet-trace tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        },
        {
            "comments": "Example that will install the dotnet-trace tool as a global tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```