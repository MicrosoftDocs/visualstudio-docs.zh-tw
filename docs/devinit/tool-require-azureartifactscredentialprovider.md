---
title: 需要-azureartifactscredentialprovider
description: devinit 工具需要-azureartifactscredentialprovider。
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
ms.openlocfilehash: 74e8775fb9dc864e8026f73e3bc75604dbf32e10
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810909"
---
# <a name="require-azureartifactscredentialprovider"></a>需要-azureartifactscredentialprovider

此 `require-azureartifactscredentialprovider` 工具會安裝 Azure Artifacts 認證提供者。 Azure Artifacts 認證提供者會自動取得將 NuGet 套件還原為 .NET 開發工作流程一部分所需的認證。 如需 Azure Artifacts 認證提供者的詳細資訊，請參閱 [這裡](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md)。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                |
| [**輸入**](#input)                              | 字串 | No       | 未使用。 如需詳細資料，請參閱下列 [輸入](#input) 。 |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                     |

### <a name="input"></a>輸入

未使用。 如果有提及，會忽略任何輸入。

### <a name="additional-options"></a>其他選項

其他選項會依原樣傳遞至認證提供者命令。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-azureartifactscredentialprovider` 是安裝最新的 Azure Artifacts 認證提供者。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
