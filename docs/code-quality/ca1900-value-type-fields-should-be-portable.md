---
title: "Ca1900： 實值類型欄位應該為可移植 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f023749c16a1c4fed36654036813007a83b21a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900：實值類型欄位應該為可移植的
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|分類|Microsoft.Portability|  
|中斷變更|中斷-可以看到在組件外部的欄位。<br /><br /> 非中斷-如果欄位不是組件外部可見。|  
  
## <a name="cause"></a>原因  
 此規則會檢查封送處理至 unmanaged 程式碼在 64 位元作業系統上時具有明確配置宣告的結構會正確地對齊。 Ia-64 不允許存取未配置的記憶體和處理程序將會損毀，如果沒有修正這種違規。  
  
## <a name="rule-description"></a>規則描述  
 具有明確配置，其中包含不當欄位會造成當機，在 64 位元作業系統上的結構。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 小於 8 個位元組的所有欄位都必須是其大小的倍數的位移和 8 個位元組的欄位或多個都必須是 8 的倍數的位移。 另一個解決方案是使用`LayoutKind.Sequential`而不是`LayoutKind.Explicit`，如果合理。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 在發生錯誤時，才應該隱藏這個警告。