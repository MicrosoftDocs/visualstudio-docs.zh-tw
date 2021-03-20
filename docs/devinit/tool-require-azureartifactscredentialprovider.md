---
title: require-azureartifactscredentialprovider
description: devinit 工具需要-azureartifactscredentialprovider。
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
ms.openlocfilehash: e5ba9847b09f06f853f48a0885de5e0d63664fac
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671606"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

> [!IMPORTANT]
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 這項功能 `devinit` 和相關聯的工具將無法再使用。 我們建議您參與我們的開發人員社區論壇，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。

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

工具的預設行為 `require-azureartifactscredentialprovider` 是安裝最新版本的 Azure Artifacts 認證提供者。

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-azureartifactscredentialprovider` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.js將會安裝 Azure Artifacts 認證提供者：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
