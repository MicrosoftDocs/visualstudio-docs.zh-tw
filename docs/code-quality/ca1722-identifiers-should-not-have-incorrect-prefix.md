---
title: CA1722:識別項名稱不應該使用不正確的前置字元
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5daf51cd8bef4910a327b8e261f15332ad6522da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921615"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722:識別項名稱不應該使用不正確的前置字元

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
識別碼有不正確的前置詞。

## <a name="rule-description"></a>規則描述
根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。

型別名稱沒有特定的前置詞, 且前面不能加上 ' C '。 此規則會報告型別名稱 (例如 ' CMyClass ') 的違規, 而且不會報告型別名稱違規, 例如 ' Cache '。

命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這種一致性可減少新軟體程式庫所需的學習曲線, 並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

## <a name="how-to-fix-violations"></a>如何修正違規
請移除識別碼中的前置詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
[CA1715識別碼應該有正確的前置詞](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)