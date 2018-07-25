---
title: MSBuild 最佳做法 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f32626f02e0381ab285d1d6ae1b3127022da438
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078195"
---
# <a name="msbuild-best-practices"></a>MSBuild 最佳做法
我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：  
  
-   處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。 例如，使用  
  
```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```
  
-   當您選取項目時，請避免使用萬用字元， 而要明確地指定檔案。 這樣會比較容易追蹤當您新增或刪除檔案時，可能發生的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [進階概念](../msbuild/msbuild-advanced-concepts.md)
