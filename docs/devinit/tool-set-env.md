---
title: set-env
description: devinit 工具需要-set-env。
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
ms.openlocfilehash: 89f62550d75a86c6d48848a31c99ca169964faa0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950419"
---
# <a name="set-env"></a>set-env

此 `set-env` 工具可用來設定要在目前進程中使用的環境變數。 環境變數只會在目前的進程中設定，而其他 `devinit` 工具在該進程中執行時，將會使用這些變數。

這項工具會使用 .NET Core `Environment.SetEnvironment` API，並具有與該 api 相同的限制。 如需詳細資訊，請參閱[](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true)的檔 `Environment.SetEnvironment` 。

## <a name="usage"></a>使用方式

| 名稱                                         | 類型   | 必要 | 值                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **評論**                                 | 字串 | No       | 選擇性批註屬性。 未使用。                                       |
| [**輸入**](#input)                          | 字串 | No       | 工具的輸入。 如需詳細資料，請參閱下列 [輸入](#input) 。               |
| [**additionalOptions**](#additional-options) | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。            |

### <a name="input"></a>輸入

此 `set-env` 工具會採用單一字串做為屬性的輸入 `input` 。 字串的格式應為分號 (; ) 分隔的機碼值組 (name = value) 和四個可能的動作，以屬性的值為基礎 `input` 。

| 動作       | 輸入            | 描述                                                                                                                                                              | 範例             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **全部列出** | 空白或省略 | 列出所有目前的環境變數。                                                                                                                           | `"input":""`        |
| **清單一** | 字串           | 依名稱列出特定環境變數的值。                                                                                                               | `"input":"foo"`     |
| **add**      | 字串           | 將環境變數的值設定為機碼值組。 新增環境變數（如果還不存在），或設定現有環境變數的值 | `"input":"foo=bar"` |
| **delete**   | 字串           | 藉由傳入空白值字串來刪除現有的環境變數。                                                                                            | `"input":"foo="`    |

`input`字串可以包含環境變數展開 `%userprofile%` ，例如，當讀取值時，就會展開。

### <a name="additional-options"></a>其他選項

 `--user``--process`可包含、或， `--machine` 以指定要設定環境變數的位置。 根據預設，我們會以使用者為目標。 如需環境變數可能目標的詳細資訊，請參閱 [>environmentvariabletarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget)。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `set-env` 是列出所有目前的環境變數。

## <a name="usage-in-a-codespace"></a>Codespace 中的使用方式

如果您使用的是 codespace，可以透過自訂檔案中的屬性，來設定 codespace 中使用的環境變數 `remoteEnv` [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `set-env` `.devinit.json` 。

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.js，將會設定環境變數， `foo` 並將其設定為值 `bar` ：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.js，則會將環境變數（值）設定 `foo` 為 `bar` 儲存在與目前進程相關聯的環境區塊中：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "additionalOptions": "--process",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.js，會顯示環境變數的值：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.js，將會列出所有環境變數：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.js將會刪除環境變數：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>將使用環境變數展開的 .devinit.json：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.js，會使用路徑操作設定環境變數值：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.js，將從儲存的複本還原路徑：
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
