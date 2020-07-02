---
title: CA1017：使用 ComVisibleAttribute 標記元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17f0a540a436316d3a4fb3b71a2a51b1c5a90a6d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535066"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017:組件必須標記 ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 元件未套用 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性會決定 COM 用戶端存取 managed 程式碼的方式。 良好的設計會要求組件明確表示 COM 的可視性。 您可以針對整個元件設定 COM 可見度，然後針對個別類型和類型成員加以覆寫。 如果屬性不存在，則 COM 用戶端可以看到元件的內容。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將屬性新增至元件。 如果您不想讓 COM 用戶端看到該元件，請套用屬性，並將其值設定為 `false` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 如果您想要顯示元件，請套用屬性，並將其值設定為 `true` 。

## <a name="example"></a>範例
 下列範例顯示已套用屬性的元件， <xref:System.Runtime.InteropServices.ComVisibleAttribute> 以防止 COM 用戶端看到它。

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>另請參閱
 [與未受管理](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)的程式碼互通，[符合用於互通的 .net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
