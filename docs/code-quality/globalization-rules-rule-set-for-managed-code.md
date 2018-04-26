---
title: 適用於 Managed 程式碼的全球化規則規則集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5f260a46d26bfec8af61a39ba8c54910a45772c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的全球化規則規則集
您可以使用 Microsoft 全球化規則規則集的重點在於可能會讓您正確出現在不同的語言、 地區設定中和文化特性的應用程式中資料的問題。 您應該包含這個規則集，如果您的應用程式當地語系化，全球化，或兩者。

|規則|描述|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|指定 MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免重複的快速鍵|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|請勿地區設定特定的字串|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|不要將常值傳遞做為當地語系化的參數|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|指定 CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|指定 IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|設定地區設定的資料類型|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|指定 StringComparison|
|[CA1308 必須](../code-quality/ca1308-normalize-strings-to-uppercase.md)|將字串標準化為大寫字母|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|使用循序的 StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|指定 P/Invoke 字串引數的封送處理|