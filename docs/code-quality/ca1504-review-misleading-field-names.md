---
title: CA1504：必須檢視可能造成誤導的欄位名稱
ms.date: 11/04/2016
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
ms.openlocfilehash: aa997ad5afb77df126cd0824d574884bef828ab6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444001"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504：必須檢視可能造成誤導的欄位名稱

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|分類|Microsoft。可維護性|
|重大變更|不中斷|

## <a name="cause"></a>原因
實例欄位的名稱開頭為 "s_"，或 `static` 的名稱（[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 `Shared`）欄位開頭為 "m_"。

## <a name="rule-description"></a>規則描述
以 "s_" 開頭的功能變數名稱會與許多使用者的靜態資料產生關聯。 同樣地，以 "m_" 開頭的功能變數名稱會與實例（成員）資料相關聯。 如需更容易維護的程式碼，名稱應遵循一般使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，藉由新增或移除 `static` 修飾詞，讓欄位與目前的尾碼一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。
