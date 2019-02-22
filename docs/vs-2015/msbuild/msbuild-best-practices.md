---
title: MSBuild 最佳做法 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2070bb696a3ce326331d01145b3ef3b54ae5ec
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780662"
---
# <a name="msbuild-best-practices"></a>MSBuild 最佳做法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
我們建議用來撰寫 MSBuild 指令碼的最佳作法如下：  
  
-   處理預設屬性值的最佳方法是使用 `Condition` 屬性，而不是宣告可以在命令列中覆寫預設值的屬性。 例如，使用  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   當您選取項目時，請避免使用萬用字元， 而要明確地指定檔案。 這樣會比較容易追蹤當您新增或刪除檔案時，可能發生的錯誤。  
  
## <a name="see-also"></a>請參閱  
 [進階概念](../msbuild/msbuild-advanced-concepts.md)
