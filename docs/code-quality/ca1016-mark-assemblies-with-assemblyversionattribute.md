---
title: CA1016：以 AssemblyVersionAttribute 標記組件
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c4f05003fdd05a4dde82d19ba11e47c35666fbc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016：以 AssemblyVersionAttribute 標記組件
|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 組件並沒有版本號碼。

## <a name="rule-description"></a>規則描述
 組件的識別是由下列資訊組成：

-   組件名稱

-   版本號碼

-   culture

-   強式名稱組件的公開金鑰。

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入版本號碼組件使用<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>屬性。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告會使用第三方或生產環境中的組件。

## <a name="example"></a>範例
 下列範例示範具有的組件<xref:System.Reflection.AssemblyVersionAttribute>套用的屬性。

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>另請參閱
 [組件版本控制](/dotnet/framework/app-domains/assembly-versioning) [How to： 建立發行者原則](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)