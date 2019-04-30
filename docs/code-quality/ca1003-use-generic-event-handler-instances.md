---
title: CA1003：使用一般事件處理常式執行個體
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: eff7b4b880526909c293e16aa32ae7045bcdf297
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780030"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：使用一般事件處理常式執行個體

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型包含的委派，會傳回 void，而且其簽章包含兩個參數 （物件的第一個和第二個是指派給 EventArgs 的類型），與包含的組件的目標.NET。

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

之前.NET，才能將自訂資訊傳遞給事件處理常式中，新的委派必須宣告所指定的類別，衍生自<xref:System.EventArgs?displayProperty=fullName>類別。 這不再是在.NET 中，則為 true。 導入的.NET Framework<xref:System.EventHandler%601?displayProperty=fullName>委派，泛型委派，讓任何類別都衍生自<xref:System.EventArgs>要與事件處理常式一起使用。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，移除委派，並使用取代其使用<xref:System.EventHandler%601?displayProperty=fullName>委派。

如果委派是由 Visual Basic 編譯器自動產生，變更要使用的事件宣告的語法<xref:System.EventHandler%601?displayProperty=fullName>委派。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1003.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示違反規則的委派。 在 Visual Basic 範例中，註解會說明如何修改範例以符合規則。 C# 範例中，範例如下顯示修改過的程式碼。

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

下列程式碼片段會移除上述的範例中，符合規則中的委派宣告。 它會取代其用於`ClassThatRaisesEvent`並`ClassThatHandlesEvent`方法使用<xref:System.EventHandler%601?displayProperty=fullName>委派。

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1005:避免在泛型類型上的過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000:不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002:不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006:無法建立巢狀成員簽章中的泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004:泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007:在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)