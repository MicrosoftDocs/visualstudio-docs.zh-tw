---
title: "CA1052： 靜態預留位置類型應該為密封 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052：靜態預留位置類型應該為密封的
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的類型只包含靜態成員宣告，且不使用[密封](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾詞。  
  
## <a name="rule-description"></a>規則描述  
 這項規則假設，只包含靜態成員的類型不是繼承，因為類型不提供任何會覆寫衍生類型中的功能。 不是繼承的型別應該用來標記`sealed`修飾詞，以禁止使用它做為基底類型。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將這個類型做為標記`sealed`。 如果您的目標[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]2.0 或更新版本，較佳的方法是標示為型別`static`。 這種方式，您可以避免必須宣告以防止建立類別的私用建構函式。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 只有型別設計為繼承，則隱藏此規則的警告。 如果沒有`sealed`修飾詞建議的類型是有用的基底類型。  
  
## <a name="example-of-a-violation"></a>發生違規的範例  
  
### <a name="description"></a>描述  
 下列範例顯示違反規則的類型。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>修正 Static 修飾詞  
  
### <a name="description"></a>描述  
 下列範例示範如何修正此規則的違規情形來標記的型別與`static`修飾詞。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1053：靜態預留位置類型不應該包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
