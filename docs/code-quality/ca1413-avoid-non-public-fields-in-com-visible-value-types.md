---
title: CA1413：避免在 COM 可見的實值類型中使用非公用欄位
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 060d8ebd26b08ef02a9986846bdab2a25a85072f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547902"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413：避免在 COM 可見的實值類型中使用非公用欄位

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|類別|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 實值型別宣告的非公用執行個體欄位。

## <a name="rule-description"></a>規則描述
 COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 檢閱資訊，不應該公開，或將具有非預期的設計或安全性影響欄位的內容。

 根據預設，所有公用實值型別會作為 COM 可見 不過，以減少誤判，此規則需要明確指示類型的 COM 的可視性。 包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設定為`false`且型別必須標示有<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，並保持隱藏的欄位，將實值型別變更為參考型別，或移除<xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性從型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，公開的欄位是否可接受的。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)