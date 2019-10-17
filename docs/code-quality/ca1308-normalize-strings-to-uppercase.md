---
title: CA1308：必須將字串標準化為大寫字母
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a217e3882cbf90365f507623347a3846ed30187a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444314"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308：必須將字串標準化為大寫字母

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|分類|Microsoft。全球化|
|重大變更|不中斷|

## <a name="cause"></a>原因
作業會將字串標準化為小寫。

## <a name="rule-description"></a>規則描述
字串應該標準化為大寫字母。 一小組字元，當它們轉換成小寫時，就無法進行來回行程。 若要進行來回行程，請將一個地區設定的字元轉換成另一個地區設定，以不同的方式表示字元資料，然後正確地從轉換後的字元中取出原始字元。

## <a name="how-to-fix-violations"></a>如何修正違規
將字串轉換成小寫的作業，以便將字串改成大寫。 例如，將 `String.ToLower(CultureInfo.InvariantCulture)` 變更為 `String.ToUpper(CultureInfo.InvariantCulture)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
當您不是根據結果來進行安全性決策時（例如，當您在 UI 中顯示時），可以放心地隱藏警告訊息。

## <a name="see-also"></a>請參閱
[全球化警告](../code-quality/globalization-warnings.md)
