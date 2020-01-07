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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592083"
---
# <a name="msbuild-best-practices"></a>MSBuild 最佳做法
我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：

- 處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。 例如，使用

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- 當您選取項目時，請避免使用萬用字元， 而要明確地指定檔案。 這樣會比較容易追蹤當您新增或刪除檔案時，可能發生的錯誤。

## <a name="see-also"></a>請參閱
- [進階概念](../msbuild/msbuild-advanced-concepts.md)
