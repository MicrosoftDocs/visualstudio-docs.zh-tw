---
title: 適用於 Managed 程式碼的全球化規則規則集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3dea6c153196223f91726eaaedcace4f62c2868c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015260"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的全球化規則規則集
您可以使用 Microsoft 全球化規則規則集將焦點放在可能會導致資料不會正確出現在不同的語言、 地區設定中和文化特性的應用程式中的問題。 您應該包含這個規則集如果當地語系化您的應用程式，全球化，或兩者。

|規則|描述|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|必須指定 MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免使用重複的快速鍵|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|不要以硬式編碼的方式加入適用於特定地區設定的字串|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|不要將常值當作已當地語系化的參數傳遞|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|必須指定 CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|必須指定 IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|必須設定資料類型的地區設定|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|必須指定 StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|必須將字串標準化為大寫字母|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|使用循序的 StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|必須指定 P/Invoke 字串引數的封送處理|