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
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
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

- 一般而言，當您選取專案時，請避免使用萬用字元。 而要明確地指定檔案。 這是因為在大部分的專案類型中，MSBuild 會在不同的時間展開萬用字元，例如新增或移除專案時，這可能會導致非預期的行為。 例外狀況是在 .NET Core SDK 樣式的專案中，這會正確地處理萬用字元。

## <a name="see-also"></a>另請參閱

- [進階概念](../msbuild/msbuild-advanced-concepts.md)
