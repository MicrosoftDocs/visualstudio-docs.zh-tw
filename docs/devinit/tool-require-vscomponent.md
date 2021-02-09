---
title: require-vscomponent
description: devinit 工具需要-vscomponent。
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
ms.openlocfilehash: 0b58e80a03828bf486e6beb4d0014f6fe2267485
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918361"
---
# <a name="require-vscomponent"></a>require-vscomponent

此 `require-vscomponent` 工具可用來將 Visual Studio 設定匯入現有的 Visual Studio。 如需詳細資訊，請參閱 `.vsconfig` [ ](../install/import-export-installation-configurations.md)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                     | 類型   | 必要 | 值                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **評論**                             | 字串 | No       | 選擇性批註屬性。 未使用。                                |
| [**輸入**](#input)                      | 字串 | No       | 的完整路徑 `.vsconfig` 。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [additionalOptions](#additional-options) | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。     |

### <a name="input"></a>輸入

`input`屬性是用來指定檔案的完整路徑 `.vsconfig` 。 如果未提及，此工具將會搜尋 `.vsconfig` 目前目錄中的，並將值傳遞至 Visual Studio 安裝程式。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-vscomponent` 是尋找 `.vsconfig` 目前目錄中的檔案，並在無訊息模式中以這些詳細資料執行 Visual Studio 安裝程式。 `require-vscomponent` 僅支援修改現有的 Visual Studio 安裝。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-vscomponent` `.devinit.json` 。

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js，將會匯入指定 .vsconfig 檔案路徑的設定：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```