---
title: CA1408：不要使用 AutoDual ClassInterfaceType
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f324eee1ae71f063ddd19d5a7f3d82af6f45c00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897009"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408：不要使用 AutoDual ClassInterfaceType
|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 的可見類型會標示<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性設為`AutoDual`值<xref:System.Runtime.InteropServices.ClassInterfaceType>。

## <a name="rule-description"></a>規則描述
 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性沒有指定，則會使用分派介面。

 除非已標記，否則所有公用的非泛型型別會顯示 com;所有的非公用與泛型型別是看不到 com。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更值<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>屬性`None`值<xref:System.Runtime.InteropServices.ClassInterfaceType>明確定義介面。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告，除非它是特定類型和其基底型別配置的未來版本中不會變更。

## <a name="example"></a>範例
 下列範例顯示違反此規則，並重新宣告要使用明確的介面之類別的類別。

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1403：自動配置類型不應該是 COM 可見](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412：ComSource 介面必須標記為 IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>另請參閱
 [限定互通的.NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [Unmanaged 程式碼的互通](/dotnet/framework/interop/index)