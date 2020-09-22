---
title: require-choco
description: devinit 工具需要-choco。
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
ms.openlocfilehash: 18ea1b08a50dc39d404058b07d7448c66a26003d
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005788"
---
# <a name="require-choco"></a>require-choco

您 `require-choco` 可以使用此工具來安裝 [chocolatey](https://chocolatey.org/)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                      |
| [**輸入**](#input)                              | 字串 | No       | 未使用。 如需詳細資料，請參閱下列 [輸入](#input) 。                           |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。 |

### <a name="input"></a>輸入

未使用。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-choco` 是安裝 chocolatey，並將它新增至 (Windows) 的路徑。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs chocolatey.",
            "tool": "require-choco"
        }
    ]
}
```