---
title: CA1504：必須檢視可能造成誤導的欄位名稱
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 1457390b523af45b5e3b23a3420cba830f45cee5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915078"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504：必須檢視可能造成誤導的欄位名稱
|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|分類|Microsoft.Maintainability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 執行個體欄位名稱開頭為"s_"或名稱`static`(`Shared`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 欄位開頭為"m_"。

## <a name="rule-description"></a>規則描述
 許多使用者關聯的靜態資料的欄位名稱開頭為"s_"。 同樣地，欄位名稱開頭為"m_"與相關聯的執行個體 （成員） 資料。 更容易維護的程式碼的名稱應遵循通常使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，讓目前的後置詞同意透過加入或移除欄位`static`修飾詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。