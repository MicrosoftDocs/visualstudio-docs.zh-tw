---
title: CA1802： 建議在適當時使用常值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8bd2d28b7bc43c1bfa6ce941d7601b956d8f487
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802：建議在適當時使用常值
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 欄位宣告`static`和`readonly`(`Shared`和`ReadOnly`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])，並初始化與在編譯時期計算的值。  
  
## <a name="rule-description"></a>規則描述  
 值`static``readonly`宣告類型的靜態建構函式呼叫時，在執行階段計算欄位。 如果`static``readonly`宣告和靜態建構函式未明確宣告，編譯器會發出初始化欄位的靜態建構函式時，會初始化欄位。  
  
 值`const`欄位會在編譯時期計算並儲存在中繼資料，來比較時，會增加執行階段效能`static``readonly`欄位。  
  
 因為指派給目標欄位的值是可在編譯時期，將宣告變更為`const`欄位，讓在編譯時期而不是在執行階段計算的值。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，取代`static`和`readonly`修飾詞搭配`const`修飾詞。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果效能不是考量，就會安全地隱藏此規則的警告，或停用規則。  
  
## <a name="example"></a>範例  
 下列範例顯示型別， `UseReadOnly`，違反此規則，並為型別， `UseConstant`，符合此規則。  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]