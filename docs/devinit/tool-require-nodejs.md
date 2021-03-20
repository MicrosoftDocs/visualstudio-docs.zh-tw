---
title: require-nodejs
description: devinit 工具需要-nodejs。
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
ms.openlocfilehash: 75690f85fb627140226242b476d70bfc4dac6ed2
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672300"
---
# <a name="require-nodejs"></a>require-nodejs

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `require-nodejs` 工具是用來透過 Node.js 組織所散發的 MSI 來安裝 [Node.js](https://nodejs.org/) 。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                     |
| [**輸入**](#input)                              | 字串 | No       | 要安裝的 Node.JS 版本。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。          |

### <a name="input"></a>輸入

`input`屬性可用來指定 Node.js 版本。 您可以在 [Node.js 下載頁面](https://nodejs.org/en/download/)中找到版本清單。 完整的版本號碼需要主要. 路徑 (例如 14.4.0) 如果有的話，安裝將會失敗。

### <a name="additional-options"></a>其他選項

您可以將其他設定選項傳入作為的值 `additionalOptions` 。 這些引數是 Node.js 的 MSI 安裝程式的直接傳遞。  

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-nodejs` 是安裝最新的 LTS 版本的節點，如 Node.JS [網站](https://nodejs.org/en/download/)中所述。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-nodejs` `.devinit.json` 。 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.js將會安裝 Node.js 的 LTS：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.js將會安裝特定版本的 Node.js：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
