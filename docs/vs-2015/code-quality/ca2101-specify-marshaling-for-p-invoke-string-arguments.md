---
title: Ca2101： 必須指定 P-invoke 字串引數的封送處理 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2cc137c2b086de5507082be34726c3eb3a9294f2
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588040"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101：必須指定 P/Invoke 字串引數的封送處理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ca2101 必須： 指定 P-invoke 字串引數的封送處理](https://docs.microsoft.com/visualstudio/code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments)。

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 平台叫用成員允許部分信任呼叫端，具有字串參數，並不會不明確封送處理字串。

## <a name="rule-description"></a>規則描述
 當您將從 Unicode 轉換成 ANSI 時，很可能並非所有的 Unicode 字元，可以表示特定的 ANSI 字碼頁中。 *自動調整的對應*嘗試替代字元，無法表示的字元來解決此問題。 使用此功能可能會造成潛在的安全性弱點，因為您無法控制所選的字元。 例如，惡意程式碼會刻意建立包含特定的字碼頁中找不到這類轉換為檔案系統的特殊字元的字元的 Unicode 字串 '..' 或 '/'。 也請注意安全性檢查的特殊字元需經常發生之前的字串轉換為 ANSI。

 自動調整的對應是未受管理的轉換，Mb 的 WChar 的預設值。 除非您明確停用自動調整的對應，您的程式碼可能包含可利用來攻擊的安全性弱點，因為此問題。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，明確封送處理字串資料類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範的方法，違反這項規則，然後顯示如何修正違規。

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]



