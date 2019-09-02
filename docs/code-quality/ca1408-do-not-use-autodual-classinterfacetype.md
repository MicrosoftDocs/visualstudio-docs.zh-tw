---
title: CA1408:不要使用 AutoDual ClassInterfaceType
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b79483e8703ea297634d0d81d5449c09b58c9fb7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921976"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408:不要使用 AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
元件物件模型 (COM) 可見類型已標記<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>為屬性設定為的`AutoDual`值<xref:System.Runtime.InteropServices.ClassInterfaceType>。

## <a name="rule-description"></a>規則描述
使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設, 如果<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>未指定屬性, 則會使用分派專用介面。

除非另有標示, 否則 COM 可以看見所有公用非泛型型別;COM 不會看到所有非公用和泛型型別。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性的值變更為的`None`值<xref:System.Runtime.InteropServices.ClassInterfaceType> , 並明確定義介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
除非確定類型的配置及其基底類型的配置不會在未來版本中變更, 否則請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示的類別會違反規則, 並將類別的重新宣告為使用明確的介面。

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1403自動設定類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412將 ComSource 介面標示為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>另請參閱

- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)