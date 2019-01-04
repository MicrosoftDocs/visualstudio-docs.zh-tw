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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4823eb7f41f99ca8af5a91c80341a51a196e1615
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919400"
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