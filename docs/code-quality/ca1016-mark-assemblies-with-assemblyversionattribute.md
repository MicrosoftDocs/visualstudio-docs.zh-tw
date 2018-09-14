---
title: CA1016：以 AssemblyVersionAttribute 標記組件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3a6ccdc84a2db30aab2352d65bd716936cb522e6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547590"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016：以 AssemblyVersionAttribute 標記組件

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|類別|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

組件並沒有版本號碼。

## <a name="rule-description"></a>規則描述

身分識別的組件包含下列資訊：

- 組件名稱

- 版本號碼

- 文化特性

- 強式名稱組件的公開金鑰。

[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入版本號碼組件使用<xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>屬性。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告可由協力廠商或在生產環境中的組件。

## <a name="example"></a>範例
 下列範例示範具有組件<xref:System.Reflection.AssemblyVersionAttribute>套用的屬性。

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>另請參閱

- [組件版本控制](/dotnet/framework/app-domains/assembly-versioning)
- [如何：建立發行者原則](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)