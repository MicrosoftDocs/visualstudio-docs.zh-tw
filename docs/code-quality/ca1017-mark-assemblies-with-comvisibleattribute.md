---
title: CA1017:組件必須標記 ComVisibleAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bc88d3932baa5bbb4a723d7a16509831d58146
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923105"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017:組件必須標記 ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|分類|Microsoft.Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
元件未<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>套用屬性。

## <a name="rule-description"></a>規則描述
屬性<xref:System.Runtime.InteropServices.ComVisibleAttribute>會決定 COM 用戶端存取 managed 程式碼的方式。 良好的設計會要求組件明確表示 COM 的可視性。 您可以針對整個元件設定 COM 可見度, 然後針對個別類型和類型成員加以覆寫。 如果屬性不存在, 則 COM 用戶端可以看到元件的內容。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將屬性新增至元件。 如果您不想讓 COM 用戶端看到該元件, 請套用屬性, 並將其值設定為`false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 如果您想要顯示元件, 請套用屬性, 並將其值設定為`true`。

## <a name="example"></a>範例
下列範例顯示已<xref:System.Runtime.InteropServices.ComVisibleAttribute>套用屬性的元件, 以防止 COM 用戶端看到它。

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)