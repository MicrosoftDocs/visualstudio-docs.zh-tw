---
title: CA1409：COM 可見類型應該是可建立的
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
ms.openlocfilehash: 402ce13b55921045f8e06d99bbe6b1e3918e457a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440274"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409：COM 可見類型應該是可建立的

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|分類|Microsoft. 互通性|
|重大變更|不中斷|

## <a name="cause"></a>原因
特別標示為「元件物件模型（COM）可見」的參考型別包含公用參數化的函式，但不包含公用預設（無參數）的函式。

## <a name="rule-description"></a>規則描述
COM 用戶端無法建立沒有公用預設函式的類型。 不過，如果有另一種方法可用來建立型別，並將它傳遞給用戶端（例如，透過方法呼叫的傳回值），則 COM 用戶端仍然可以存取型別。

此規則會忽略衍生自 <xref:System.Delegate?displayProperty=fullName> 的類型。

根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請新增公用預設的函式，或從類型移除 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果提供其他方式來建立物件並將其傳遞給 COM 用戶端，則可以安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
[CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>請參閱

- [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
