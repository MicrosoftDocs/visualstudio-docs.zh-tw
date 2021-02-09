---
title: devinit 設定檔
description: Devinit 資訊清單檔案的檔。 .devinit.js
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 47859d00861c2361ed03931bf1417e22425d6e68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908121"
---
# <a name="devinit-configuration-file"></a>devinit 設定檔

檔案 `.devinit.json` 會定義您的應用程式執行和建立所需的全系統相依性。 整個系統的相依性，例如 Node.js、SQL Server、IIS、RabbitMQ、Docker 等等。這些是您通常會安裝在開發人員方塊上的專案，而不是由特定存放庫安裝。 它不是定義應用程式特定相依性的地方，就像您在套件管理員（例如 NuGet 或 NPM）中所做的一樣。 不過，您可以在其中定義您需要這些封裝管理員的位置。

## <a name="file-location"></a>檔案位置

此 `devinit init` 命令是透過檔案驅動 `.devinit.json` 。 依預設，會 `devinit` 在下列位置尋找檔案：

* {目前的目錄} \\.devinit.js開啟
* {目前的目錄} \\devinit.js開啟
* {目前的目錄} \\ 。devinit \\.devinit.js開啟
* {目前的目錄} \\ 。devinit \\devinit.js開啟
* {目前的目錄} \\devinit \\.devinit.js開啟
* {目前的目錄} \\devinit \\devinit.js開啟
* {目前的目錄} \\ 。devcontainer \\.devinit.js開啟
* {目前的目錄} \\ 。devcontainer \\devinit.js開啟

> [!NOTE]
> 如果找到多個預設檔案，則 devinit 會使用上述清單中第一個出現的檔案。

您 `.devinit.json` 也可以透過選項明確指定此檔案 `--file` / `-f` 。

### <a name="directories-and-relative-paths"></a>目錄和相對路徑

路徑是相對於執行 devinit 的位置。 這通常是目前執行所在的工作目錄 `devinit` 。

## <a name="file-format"></a>檔案格式
在中 `.devinit.json` ，您可以指定多個要執行的工具。 在 `run` 區段中，您可以放入任何數目的物件。 您可以在我們的範例中，使用我們所有的工具來瞭解這種情況的範例 [.devinit.js](sample-all-tool.md) 。

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
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

如需使用 devinit 的更多範例，請參閱 [範例一節](sample-readme.md)。
