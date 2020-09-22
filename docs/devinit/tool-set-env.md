---
title: set-env
description: devinit 工具需要-set-env。
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
ms.openlocfilehash: 2f4ec5489f22e94ad8f57f22ddc7742dc0ae3ade
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005992"
---
# <a name="set-env"></a>set-env

此 `set-env` 工具可用來設定要在目前進程中使用的環境變數。 環境變數只會在目前的進程中設定，而其他 `devinit` 工具在該進程中執行時，將會使用這些變數。

這項工具會使用 .NET Core `Environment.SetEnvironment` API，並具有與該 api 相同的限制。 如需詳細資訊，請參閱[documentation](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true)的檔 `Environment.SetEnvironment` 。

## <a name="usage"></a>使用方式

| 名稱                                         | 類型   | 必要 | 值                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **評論**                                 | 字串 | No       | 選擇性批註屬性。 未使用。                                       |
| [**輸入**](#input)                          | 字串 | No       | 工具的輸入。 如需詳細資料，請參閱下列 [輸入](#input) 。               |
| [**additionalOptions**](#additional-options) | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。  |

### <a name="input"></a>輸入

此 `set-env` 工具會採用單一字串做為屬性的輸入 `input` 。 字串的格式應為分號 (; ) 分隔的機碼值組 (name = value) 和四個可能的動作，以屬性的值為基礎 `input` 。

| 動作       | 輸入            | 描述                                                                                                                                                              | 範例             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **全部列出** | 空白或省略 | 列出所有目前的環境變數。                                                                                                                              | `"input":""`        |
| **清單一** | 字串           | 依名稱列出特定環境變數的值。                                                                                                               | `"input":"foo"`     |
| **add**      | 字串           | 將環境變數的值設定為機碼值組。 新增環境變數（如果還不存在），或設定現有環境變數的值 | `"input":"foo=bar"` |
| **delete**   | 字串           | 藉由傳入空白值字串來刪除現有的環境變數。                                                                                            | `"input":"foo="`    |

`input`字串可以包含環境變數展開 `%userprofile%` ，例如，當讀取值時，就會展開。

### <a name="additional-options"></a>其他選項

未使用。

## <a name="usage-in-a-codespace"></a>Codespace 中的使用方式

如果您使用的是 codespace，可以透過 customizating 檔案中的屬性，來設定 codespace 中使用的環境變數 `remoteEnv` [`.devcontainer.json`](https://docs.microsoft.com/visualstudio/codespaces/reference/configuring) 。

## <a name="example-usage"></a>使用方式範例

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```
