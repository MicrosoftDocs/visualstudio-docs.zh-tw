---
title: require-azurecli
description: devinit 工具需要-azurecli。
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
ms.openlocfilehash: 799f1f8153d132f8490bc4fe99c17a256893a6be
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671599"
---
# <a name="require-azurecli"></a>require-azurecli

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

此 `require-azurecli` 工具是用來透過 AZURE CLI MSI 來安裝 [Azure CLI](/cli/azure/?view=azure-cli-latest&preserve-view=true) 。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                          |
| [**輸入**](#input)                              | 字串 | No       | 未使用。 如需詳細資料，請參閱下列 [輸入](#input) 。                               |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。     |

### <a name="input"></a>輸入

未使用。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-azurecli` 是安裝最新版本的 Azure CLI，並將其新增至 `PATH` 。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-azurecli` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>將會安裝 Azure CLI 的 .devinit.js：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```