---
title: CA1504:查看誤導的功能變數名稱 |Microsoft Docs
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
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607755"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504:必須檢閱可能造成誤導的欄位名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|分類|Microsoft。可維護性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 實例欄位的名稱是以 "s_" 開頭，或 `static` 的名稱（[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中的 `Shared`）欄位開頭為 "m_"。

## <a name="rule-description"></a>規則描述
 以 "s_" 開頭的功能變數名稱會與許多使用者的靜態資料產生關聯。 同樣地，以 "m_" 開頭的功能變數名稱會與實例（成員）資料相關聯。 如需更容易維護的程式碼，名稱應遵循一般使用的慣例。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用適當的前置詞重新命名欄位。 或者，藉由新增或移除 `static` 修飾詞，讓欄位與目前的尾碼一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。
