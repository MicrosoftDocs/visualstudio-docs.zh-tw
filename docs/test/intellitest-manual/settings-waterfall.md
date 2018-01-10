---
title: "設定瀑布圖 | Microsoft IntelliTest 開發人員測試工具 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Settings waterfall
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: b782987dd3bf1b96c063d43d80634289e5165af7
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="settings-waterfall"></a>設定瀑布圖

設定瀑布圖的概念，表示使用者可以在**組件**、**裝置**和**探索**層級指定設定： 

* 組件 - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* 裝置 - [PexClass](attribute-glossary.md#pexclass)
* 探索 - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

在**組件**層級指定的設定會影響該組件下的所有裝置和探索。 在**裝置**層級指定的設定會影響該裝置下的所有探索。 子設定優先：如果**組件**和**裝置**層級都定義了設定，則使用**裝置**的設定。

請注意，某些設定專屬於**組件**層級或**裝置**層級。 

**範例**

```
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500 
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>有任何意見反應嗎？

您可以在 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)** 張貼想法和功能要求。
