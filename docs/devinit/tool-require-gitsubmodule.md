---
title: 需要-gitsubmodule
description: devinit 工具需要-gitsubmodule。
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
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810127"
---
# <a name="require-gitsubmodule"></a>需要-gitsubmodule

此 `require-gitsubmodule` 工具會為指定的檔案還原 Git 子模組 `.gitmodules` 。 `.gitmodules`如果未傳遞任何輸入，則會使用根目錄中的本機檔案。 請 [在這裡](https://git-scm.com/book/en/v2/Git-Tools-Submodules)閱讀有關 Git 子模組的詳細資訊。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                |
| [**輸入**](#input)                              | 字串 | No       | `.gitmodules` 檔案的完整路徑。 如需詳細資料，請參閱下列 [輸入](#input) 。               |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。                     |

### <a name="input"></a>輸入

（選擇性） `input` 用來取得 `.gitmodules` 還原的檔案路徑。 如果 `input` 省略，則會使用根目錄檔案 `.gitmodules` 。

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

此工具的預設行為 `require-gitsubmodule` 是還原 file 中提及的 git 子模組 `.gitmodules` 。

## <a name="example-usage"></a>使用方式範例

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
