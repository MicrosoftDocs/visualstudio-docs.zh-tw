---
title: CA1409:Com 可見類型應該是可建立的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05dbe964a16f838088fe8b053d59c1916daf38f7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933715"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409:Com 可見類型應該是可建立的

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 參考型別包含公用參數化建構函式，但不包含公用預設 （無參數） 建構函式。

## <a name="rule-description"></a>規則描述
 COM 用戶端無法建立沒有公用預設建構函式的類型。 不過，類型可以仍可存取由 COM 用戶端如果另一個方法可建立類型，並將它傳遞給用戶端 （例如，透過方法呼叫的傳回值）。

 此規則會忽略型別衍生自<xref:System.Delegate?displayProperty=fullName>。

 根據預設，以下是為 COM 所見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入公用預設建構函式，或移除<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>從型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，如果提供的其他方式建立，並將物件傳遞給 COM 用戶端。

## <a name="related-rules"></a>相關的規則
 [CA1017:組件必須標記 comvisibleattribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱

- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)