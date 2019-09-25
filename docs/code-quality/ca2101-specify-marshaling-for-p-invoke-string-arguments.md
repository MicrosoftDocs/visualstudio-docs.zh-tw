---
title: CA2101:必須指定 P-Invoke 字串引數的封送處理
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49c9dfdac1d8d8aec8ec32df7374b5ae0a28e92
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233017"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101:必須指定 P/Invoke 字串引數的封送處理

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|分類|Microsoft.Globalization|
|重大變更|不中斷|

## <a name="cause"></a>原因
平台叫用成員允許部分信任的呼叫端、具有字串參數，而且不會明確地封送處理字串。

## <a name="rule-description"></a>規則描述
當您從 Unicode 轉換成 ANSI 時，可能並非所有的 Unicode 字元都可以在特定的 ANSI 字碼頁中表示。 自動*調整對應*會以字元取代無法表示的字元，來嘗試解決此問題。 使用這項功能可能會造成潛在的安全性弱點，因為您無法控制所選擇的字元。 例如，惡意程式碼可能會刻意建立一個 Unicode 字串，其中包含在特定字碼頁中找不到的字元，而這些字元會轉換成檔案系統的特殊字元，例如 ' ... ' 或 '/'。 另請注意，在字串轉換成 ANSI 之前，會經常發生特殊字元的安全性檢查。

自動調整對應是非受控轉換的預設值，WChar 為 Mb。 除非您明確停用自動調整對應，否則您的程式碼可能會因為此問題而包含可利用的安全性弱點。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請明確地封送處理字串資料類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反此規則的方法，並顯示如何修正違規。

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]