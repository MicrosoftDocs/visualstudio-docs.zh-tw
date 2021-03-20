---
title: require-nuget
description: devinit 工具需要-nuget。
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
ms.openlocfilehash: c49f77fe8b32ce6617b34d522e36cc5988d0c33c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672286"
---
# <a name="require-nuget"></a>require-nuget

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `require-nuget` 工具會下載 NUGET CLI 並將它新增至 `PATH` 。 NuGet CLI 提供 NuGet 功能的完整範圍，以安裝、建立、發行和管理套件，而不需要對專案檔進行任何變更。 [在此](/nuget/reference/nuget-exe-cli-reference)閱讀更多有關 NuGet CLI 的資訊。

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
以下是如何使用執行的範例 `require-nuget` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-a-specified-version-of-nuget"></a>.devinit.js將會安裝指定版本的 NuGet：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
        }
    ]
}
```