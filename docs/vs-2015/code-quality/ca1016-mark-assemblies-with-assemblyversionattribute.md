---
title: CA1016:組件必須標記 assemblyversionattribute |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4fbe2ef81dbb1dd5be15b6a0ac4b8cc1df96206a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939937"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016:組件必須標記 AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 組件並沒有版本號碼。

## <a name="rule-description"></a>規則描述
 身分識別的組件包含下列資訊：

- 組件名稱

- 版本號碼

- culture

- 強式名稱組件的公開金鑰。

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入版本號碼組件使用<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>屬性。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告可由協力廠商或在生產環境中的組件。

## <a name="example"></a>範例
 下列範例示範具有組件<xref:System.Reflection.AssemblyVersionAttribute>套用的屬性。

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>另請參閱
 [組件版本控制](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [How to:建立發行者原則](http://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
