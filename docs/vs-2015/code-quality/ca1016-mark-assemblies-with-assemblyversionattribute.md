---
title: CA1016：使用 AssemblyVersionAttribute 標記元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1498624d4f79a60854a624ee5c4053a3343f515
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663162"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016：以 AssemblyVersionAttribute 標記組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 元件沒有版本號碼。

## <a name="rule-description"></a>規則描述
 元件的身分識別是由下列資訊所組成：

- 組件名稱

- 版本號碼

- culture

- 公開金鑰（適用于強式名稱的元件）。

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用 <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 屬性，將版本號碼新增至元件。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿針對協力廠商或生產環境中所使用的元件，隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示已套用 <xref:System.Reflection.AssemblyVersionAttribute> 屬性的元件。

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>請參閱
 [元件版本控制](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)[如何：建立發行者原則](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
