---
title: devinit 設定檔
description: Devinit 資訊清單檔案的檔。 .devinit.js
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3d7df98dc6ebfb59aa78e6f0c546632bf84596f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809697"
---
# <a name="devinit-configuration-file"></a>devinit 設定檔

## <a name="file-location"></a>檔案位置

此 `devinit.exe init` 命令是透過檔案 _ 上的.devinit.js_ 驅動。 依預設，會 `devinit.exe` 在下列位置尋找檔案：

- _{目前的目錄}\\_
- _{目前的目錄} \\ 。devinit\\_
- _{目前的目錄} \\ 。devcontainer\\_

_._ 在中，可以省略目錄和檔案名。

您也可以透過選項明確指定檔案_上_的.devinit.js`--file` / `-f` 。

### <a name="directories-and-relative-paths"></a>目錄和相對路徑

路徑是相對於執行 devinit 的位置。 這通常是目前執行所在的工作目錄 `devinit` 。

## <a name="file-format"></a>檔案格式

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>屬性值

| 名稱         | 類型   | 必要 | 值                              |
|--------------|--------|----------|------------------------------------|
| **評論** | 字串 | No       | 檔案的批註。             |
| **運行**      | array  | 是      | [RunTool 物件](#run-tool-object) |

#### <a name="run-tool-object"></a>執行工具物件

| 名稱                  | 類型   | 必要 | 值                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **評論**          | 字串 | No       | 工具專案的批註。                                                                               |
| **工具**              | 字串 | 是      | 工具名稱。 如需 `devinit list` 可用工具的清單，請參閱命令。                            |
| **input**             | 字串 | No       | 工具輸入。 因工具而異。 例如，所需的版本、封裝識別碼、檔案名或資料夾。|
| **additionalOptions** | 字串 | No       | 要傳遞至工具的其他命令列引數。                                                |

## <a name="examples"></a>範例

如需使用 devinit 的更多範例，請參閱 [範例一節](/samples)。
