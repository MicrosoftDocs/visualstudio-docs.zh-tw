---
title: CA1016：以 AssemblyVersionAttribute 標記組件
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 85a8d2d9efe83f62bd0bd40021ffe0e752cf4666
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441612"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016：以 AssemblyVersionAttribute 標記組件

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|分類|Microsoft. Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

元件沒有版本號碼。

## <a name="rule-description"></a>規則描述

元件的身分識別是由下列資訊所組成：

- 組件名稱

- 版本號碼

- culture

- 公開金鑰（適用于強式名稱的元件）。

.NET 會使用版本號碼來唯一識別元件，並系結至強式名稱元件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用 <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> 屬性，將版本號碼新增至元件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿針對協力廠商或生產環境中所使用的元件，隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示已套用 <xref:System.Reflection.AssemblyVersionAttribute> 屬性的元件。

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>請參閱

- [元件版本控制](/dotnet/framework/app-domains/assembly-versioning)
- [如何：建立發行者原則](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)
