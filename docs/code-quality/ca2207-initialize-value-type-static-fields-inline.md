---
title: CA2207:必須將實值類型的靜態欄位內嵌初始化
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2caeb78af5fed0c74c02c6e3f578fa34e765355
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920364"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207:必須將實值類型的靜態欄位內嵌初始化

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
實值型別會宣告明確的靜態函數。

## <a name="rule-description"></a>規則描述
當宣告實值型別時, 它會經歷預設的初始化, 其中所有的數值型別欄位都設定為零, 而且所有的參考型別`null`欄位`Nothing`都會設定為 (在 Visual Basic 中)。 只有在呼叫類型的實例或靜態成員之前, 才保證會執行明確的靜態函數。 因此, 如果在沒有呼叫實例的函式的情況下建立型別, 則不保證會執行靜態的函數。

如果所有靜態資料都是以內嵌方式初始化, 而且未宣告明確的C#靜態函式, 則`beforefieldinit`和 Visual Basic 編譯器會將旗標加入至 MSIL 類別定義。 編譯器也會加入包含靜態初始化程式碼的私用靜態函式。 這個私用靜態的函式保證會在存取類型的任何靜態欄位之前執行。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請在宣告所有靜態資料時將其初始化, 並移除靜態的函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
[CA1810 必須初始化參考型別靜態欄位內嵌](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)