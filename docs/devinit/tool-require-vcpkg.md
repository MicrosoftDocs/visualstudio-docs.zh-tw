---
title: require-vcpkg
description: devinit 工具需要-vcpkg。
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
ms.openlocfilehash: 222e1af34c759f4bf0fbac61f03a38ba8a24ffbe
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400250"
---
# <a name="require-vcpkg"></a>require-vcpkg

此 `require-vcpkg` 工具是用來安裝 [vcpkg](https://github.com/microsoft/vcpkg)。

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

工具的預設行為 `require-vcpkg` 是安裝 vcpkg，並將它新增至 (Windows) 的路徑。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Installs vcpkg.",
            "tool": "require-vcpkg"
        }
    ]
}
```
