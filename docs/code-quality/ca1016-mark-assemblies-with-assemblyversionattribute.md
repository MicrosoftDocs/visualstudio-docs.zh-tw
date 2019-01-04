---
title: CA1016:組件必須標記 AssemblyVersionAttribute
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: b4361671eb884fada158cb5032b667ea03522b87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912700"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016:組件必須標記 AssemblyVersionAttribute

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

.NET Framework 使用的版本號碼，來唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

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