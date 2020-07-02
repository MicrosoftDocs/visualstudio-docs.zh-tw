---
title: CA1504 必須：檢查誤導的功能變數名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d375b64bbc877cb377157f13b3e4cfa7c7cf1592
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547871"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504:必須檢閱可能造成誤導的欄位名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|類別|Microsoft。可維護性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 實例欄位的名稱開頭為 "s_"，或 `static` （ `Shared` 在中）欄位的名稱開頭 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 為 "m_"。

## <a name="rule-description"></a>規則描述
 以 "s_" 開頭的功能變數名稱會與許多使用者相關聯的靜態資料。 同樣地，以 "m_" 為開頭的功能變數名稱會與實例（成員）資料相關聯。 如需更容易維護的程式碼，名稱應遵循一般使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，藉由新增或移除修飾詞，讓欄位與目前的尾碼一致 `static` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
