---
title: azurecli-login
description: devinit 工具 azurecli-登入。
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
ms.openlocfilehash: 304c7b12e3b290c3e47857877b050b18873e3934
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672308"
---
# <a name="azurecli-login"></a>azurecli-login

此 `azurecli-login` 工具可用來透過 [Azure CLI](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest)登入 Azure Active Directory。 此工具會使用 Azure CLI 命令： `az login --use-device-code` ，若要完成登入，您必須遵循列印到主控台的指示。

## <a name="usage"></a>使用方式

如果兩個屬性都省略或空白，則工具將會遵循如下所述的 [預設](#default-behavior) 行為。

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

此工具的預設行為 `azurecli-login` 是安裝最新版本的 Azure CLI，並將其新增至僅 (Windows) 的路徑。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `azurecli-login` `.devinit.json` 。 

#### <a name="devinitjson-that-will-trigger-azure-login"></a>將會觸發 Azure 登入的 .devinit.js：

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```