---
title: CA1308:必須將字串標準化為大寫字母
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
ms.openlocfilehash: 4e8d8b5b522f805bd7e8826cea5ced394c50064f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546670"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308:必須將字串標準化為大寫字母

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 作業會正規化為小寫字串。

## <a name="rule-description"></a>規則描述
 字串應該標準化為大寫字母。 小組的字元，它們會轉換成小寫字母時，無法構成來回行程。 若要在來回行程將字元轉換從一個地區設定為以不同的方式表示字元資料的另一個地區設定，然後以精確地表示會擷取原始的字元從已轉換的字元。

## <a name="how-to-fix-violations"></a>如何修正違規
 變更作業，將字串轉換成小寫，以便將字串轉換成改為大寫。 例如，將 `String.ToLower(CultureInfo.InvariantCulture)` 變更為 `String.ToUpper(CultureInfo.InvariantCulture)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏警告訊息，當您不進行 （例如，當您要將它顯示在 UI 中） 的結果為基礎的安全性決策。

## <a name="see-also"></a>另請參閱
 [全球化警告](../code-quality/globalization-warnings.md)