---
title: T4 CleanUpBehavior 指示詞
description: 瞭解 CleanUpBehavior 指示詞，以及如何在處理文字模板之後刪除 appDomain。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 078b688c238bea47e4ab38b3302708bf5e5189cf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386341"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 指示詞

若要在處理文字範本後刪除 appDomain，請加入下列幾行：

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

文字範本是在與主機處理序不同的 appDomain 中處理。 大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。 但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。

這會減緩文字處理的速度，不過，其有助於確保處置資源。

這個指示詞只能在 Visual Studio 主機中起作用。
