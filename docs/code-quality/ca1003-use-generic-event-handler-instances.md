---
title: CA1003：必須使用一般事件處理常式執行個體
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
ms.openlocfilehash: 42e40acfc8034f27c8b9131b6d5c8f8bb2f95dcb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441728"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：必須使用一般事件處理常式執行個體

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|分類|Microsoft. Design|
|重大變更|中斷|

## <a name="cause"></a>原因

類型包含傳回 void 的委派，其簽章包含兩個參數（第一個是物件，第二個是可指派給 EventArgs 的類型），而包含的元件則是以 .NET 為目標。

根據預設，此規則只會查看外部可見的類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

在 .NET 之前，為了將自訂資訊傳遞至事件處理常式，必須宣告新的委派，以指定衍生自 @no__t 0 類別的類別。 在 .NET 中，泛型 <xref:System.EventHandler%601?displayProperty=fullName> 委派可讓衍生自 <xref:System.EventArgs> 的任何類別與事件處理常式一起使用。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請移除委派，並使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派來取代其使用方式。

如果委派是由 Visual Basic 編譯器自動產生，請將事件宣告的語法變更為使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示違反規則的委派。 在 Visual Basic 範例中，批註會說明如何修改範例以符合規則。 C#範例中的範例會顯示修改過的程式碼。

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

下列程式碼片段會移除上一個範例中符合規則的委派宣告。 它會使用 @no__t 2 委派來取代 @no__t 0 和 @no__t 1 方法中的使用方式。

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>相關規則

- [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)
