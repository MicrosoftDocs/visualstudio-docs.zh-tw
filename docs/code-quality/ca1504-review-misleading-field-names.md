---
title: CA1504:必須檢閱可能造成誤導的欄位名稱
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da99bab4235028f75146be1807162e93759d3eb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926458"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504:必須檢閱可能造成誤導的欄位名稱

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|分類|Microsoft.Maintainability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 執行個體欄位名稱開頭為"s_"或名稱`static`(`Shared`在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 欄位開頭為"m_"。

## <a name="rule-description"></a>規則描述
 欄位名稱開頭為"s_"是由許多使用者關聯的靜態資料。 同樣地，欄位名稱開頭為"m_"是資料執行個體 （成員） 相關聯。 對於更容易維護的程式碼，名稱應該遵循通常使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，請同意透過加入或移除目前的後置詞欄位`static`修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。