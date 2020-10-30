---
title: MSBuild 最佳做法 | Microsoft Docs
description: 瞭解撰寫 MSBuild 腳本的最佳作法，例如使用條件屬性而不使用萬用字元。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047659"
---
# <a name="msbuild-best-practices"></a>MSBuild 最佳做法

我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：

- 處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。 例如，使用

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- 一般情況下，請避免在選取專案時使用萬用字元。 而要明確地指定檔案。 這是因為在大部分的專案類型中，MSBuild 會在不同的時間展開萬用字元，例如新增或移除專案時，可能會導致非預期的行為。 例外狀況是在 .NET Core SDK 樣式的專案中，這會正確處理萬用字元。

## <a name="see-also"></a>請參閱

- [進階概念](../msbuild/msbuild-advanced-concepts.md)
