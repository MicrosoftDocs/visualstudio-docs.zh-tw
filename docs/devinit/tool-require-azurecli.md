---
title: require-azurecli
description: devinit 工具需要-azurecli。
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
ms.openlocfilehash: da6ce656e552a7df0b02fd4a0df3a1fb78871607
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672143"
---
# <a name="require-azurecli"></a>require-azurecli

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

此工具的預設行為 `require-azurecli` 是安裝最新版本的 Azure CLI，並將其新增至僅 (Windows) 的路徑。

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