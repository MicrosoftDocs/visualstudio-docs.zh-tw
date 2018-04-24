---
title: T4 CleanUpBehavior 指示詞
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cb9c92aad2518a9e16adbcb37006c62c421c4361
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指示詞

若要在處理文字範本後刪除 appDomain，請加入下列幾行：

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

文字範本是在與主機處理序不同的 appDomain 中處理。 大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。 但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。

這會減緩文字處理的速度，不過，其有助於確保處置資源。

這個指示詞只能在 Visual Studio 主機中起作用。