---
title: CA1017：以 ComVisibleAttribute 標記組件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d2e720bf4e0bd613b5f31b82e7c50084b1b6d3c1
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548552"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017：以 ComVisibleAttribute 標記組件

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|類別|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 組件沒有<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>套用屬性。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性會判斷 COM 用戶端存取 managed 程式碼的方式。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件設定，並再覆寫為個別的類型和類型成員。 如果屬性不存在，就有一個組件的內容可對 COM 用戶端。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入組件中的屬性。 如果您不想要對 COM 用戶端可見的組件，將屬性套用，並將其值設定為`false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 如果您想要顯示的組件時，將屬性套用，並將其值設定為`true`。

## <a name="example"></a>範例
 下列範例示範具有組件<xref:System.Runtime.InteropServices.ComVisibleAttribute>套用以防止它不會對 COM 用戶端顯示的屬性。

 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)