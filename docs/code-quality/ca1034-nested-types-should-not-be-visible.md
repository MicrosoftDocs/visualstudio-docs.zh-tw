---
title: "CA1034： 巢狀的類型不應該為可見 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc35514eab2344c086305ec88435ff8a32285e4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034：巢狀類型不應為可見
|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 外部可見類型包含外部可見的型別宣告。 巢狀的列舉與受保護的類型免套用此規則。  
  
## <a name="rule-description"></a>規則描述  
 巢狀型別是另一種類型的範圍內宣告的類型。 巢狀型別可用於封裝包含型別的私用實作詳細資料。 因為有這樣的用途，所以巢狀類型不應為外部可見的。  
  
 不會使用外部可見的巢狀的類型的邏輯群組，或避免發生名稱衝突。相反地，使用命名空間。  
  
 巢狀型別包含成員存取範圍，某些程式設計人員不清楚地了解的概念。  
  
 受保護的類型可以用於子類別以及進階自訂化情節中的巢狀的類型。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 如果您不想要為外部可見的巢狀的類型，請變更型別的存取範圍。 否則，請從其父代移除巢狀的類型。 如果巢狀的目的是要分類的巢狀的類型，請改為建立在階層中使用命名空間。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]