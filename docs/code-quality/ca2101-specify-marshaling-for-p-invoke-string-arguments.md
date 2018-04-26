---
title: Ca2101： 必須指定 P Invoke 字串引數的封送處理
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc32aedf38430ab3ce9657f3a7e4d8d9e416fa57
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101：必須指定 P/Invoke 字串引數的封送處理
|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|分類|Microsoft.Globalization|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 平台叫用成員允許部分信任呼叫端，具有字串參數，並不會不明確封送處理字串。

## <a name="rule-description"></a>規則描述
 當您將從 Unicode 轉換為 ANSI 時，很可能不是所有的 Unicode 字元，可以將特定的 ANSI 字碼頁中表示。 *自動調整的對應*嘗試解決這個問題的替代字元，無法表示的字元。 使用此功能可能會造成潛在的安全性弱點，因為您無法控制會選擇的字元。 例如，惡意程式碼可以刻意建立 Unicode 字串，包含特定字碼頁中找不到這類轉換成檔案系統中的特殊字元的字元 '..' 或 '/'。 請注意安全性檢查的特殊字元經常發生之前將字串轉換為 ANSI。

 自動調整的對應是 unmanaged 轉換到 Mb WChar 的預設值。 除非您明確停用自動調整的對應，您的程式碼可能包含利用的安全性弱點，因為此問題。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，明確封送處理字串資料類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範的方法違反此規則，然後示範如何修正違規。

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]