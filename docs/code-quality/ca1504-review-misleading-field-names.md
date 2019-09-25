---
title: CA1504:必須檢閱可能造成誤導的欄位名稱
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
ms.openlocfilehash: 31c147c67854dd59f1fb7c9202f553edfb4a77a8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234499"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504:必須檢閱可能造成誤導的欄位名稱

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|分類|Microsoft.Maintainability|
|重大變更|不中斷|

## <a name="cause"></a>原因
實例欄位的名稱開頭為 "s_"，或欄位的名稱`static` `Shared` [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]開頭為 "m_"。

## <a name="rule-description"></a>規則描述
以 "s_" 開頭的功能變數名稱會與許多使用者的靜態資料產生關聯。 同樣地，以 "m_" 開頭的功能變數名稱會與實例（成員）資料相關聯。 如需更容易維護的程式碼，名稱應遵循一般使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，藉由新增或移除`static`修飾詞，讓欄位與目前的尾碼一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。