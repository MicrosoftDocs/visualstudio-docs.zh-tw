---
title: MSBuild 最佳做法 | Microsoft Docs
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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263145"
---
# <a name="msbuild-best-practices"></a>MSBuild 最佳做法

我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：

- 處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。 例如，使用

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- 通常，在選擇專案時，請避免使用萬用字元。 而要明確地指定檔案。 這是因為在大多數專案類型中，MSBuild 會在不同時間（例如添加或刪除項時）擴展萬用字元，這可能導致意外行為。 例外情況是 .NET Core SDK 樣式專案，這些專案正確處理萬用字元。

## <a name="see-also"></a>另請參閱

- [進階概念](../msbuild/msbuild-advanced-concepts.md)
