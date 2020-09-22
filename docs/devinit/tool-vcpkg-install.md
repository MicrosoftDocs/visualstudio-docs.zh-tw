---
title: vcpkg-install
description: devinit tool vcpkg-安裝。
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
ms.openlocfilehash: 7c974b5747c38231ff4115aba17a8e3728672851
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005985"
---
# <a name="vcpkg-install"></a>vcpkg-install

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

其他選項會直接傳遞至 [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) 命令，並記載于 [vcpkg GitHub](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)存放庫中。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `vcpkg-install` 是「錯誤」（ `input` required）。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
