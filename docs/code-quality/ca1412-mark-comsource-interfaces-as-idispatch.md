---
title: CA1412:ComSource 介面必須標記為 IDispatch
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 61a7042c4eae547a9da64503301351e96681f328
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013960"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412:ComSource 介面必須標記為 IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型會標示<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性和至少一個指定的介面不以標示<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性設為`InterfaceIsDispatch`值。

## <a name="rule-description"></a>規則描述

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> 用來識別類別會公開元件物件模型 (COM) 用戶端的事件介面。 這些介面必須公開為`InterfaceIsIDispatch`讓 Visual Basic 6 COM 用戶端接收事件通知。 根據預設，如果介面不以標示<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，它會公開為雙重介面。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，加入或修改<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>屬性，讓其值設定為所指定的所有介面 InterfaceIsIDispatch<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例示範類別其中一個介面違反規則的位置。

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>相關的規則

[CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)