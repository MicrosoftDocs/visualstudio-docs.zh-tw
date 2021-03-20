---
title: require-vscomponent
description: devinit 工具需要-vscomponent。
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7d6609c49efb9f77c9823ca3f703b8843ddb753e
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672670"
---
# <a name="require-vscomponent"></a>require-vscomponent

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

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

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 

| 名稱                      | 類型      | 必要 | 值                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --installPath             | 字串    | No       | 您要修改之 Visual Studio 實例的安裝路徑。                                                                                                                       |

如果未指定安裝路徑，則當您的電腦上有多個實例時，工具將會修改電腦上最早安裝的 Visual Studio。 

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

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>.devinit.js，則會將指定之 .vsconfig 檔案路徑的設定匯入至透過安裝路徑指定的 Visual Studio 實例：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```