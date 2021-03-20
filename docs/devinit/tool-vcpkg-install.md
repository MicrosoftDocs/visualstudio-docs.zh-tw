---
title: vcpkg-install
description: devinit tool vcpkg-安裝。
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
ms.openlocfilehash: 8a4cbe6bd1da12985da87d2f872dc74f988ef213
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672649"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `vcpkg-install` 工具可用來取得 C/c + + 程式庫 (稱為埠) 使用 [vcpkg](https://github.com/microsoft/vcpkg)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                   |
| [**輸入**](#input)                              | 字串 | Yes      | 要安裝的套件 (s) 。 如需詳細資料，請參閱下列 [輸入](#input) 。                       |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                        |

### <a name="input"></a>輸入

`input`屬性應該是 `name` 要安裝的， `vcpkg` 或是用來安裝多個封裝的空格分隔名稱清單。 您可以在 [Vcpkg GitHub](https://github.com/microsoft/vcpkg/tree/master/ports)存放庫中找到可用的埠清單。

### <a name="additional-options"></a>其他選項

其他選項會直接傳遞至 [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) 命令，並記載于 [vcpkg GitHub](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)存放庫中。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `vcpkg-install` 是在需要時發生錯誤 `input` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `vcpkg-install` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.js將會安裝 sdl2 埠：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>會安裝多個埠的 .devinit.js：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```