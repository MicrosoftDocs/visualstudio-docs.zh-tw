---
title: 適用於 Managed 程式碼的全球化規則規則集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 03bd4d286ab0bcba37c9c1761c0331ce1347f313
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89219669"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的全球化規則規則集

使用 Microsoft 全球化規則規則集，將焦點放在可能導致應用程式中的資料無法在不同語言、地區設定和文化特性中正確顯示的問題。 如果您的應用程式已當地語系化、全球化或兩者皆是，則應包含此規則集。

|規則|描述|
|----------|-----------------|
|[CA1300](../code-quality/ca1300.md)|必須指定 MessageBoxOptions|
|[CA1301](../code-quality/ca1301.md)|避免使用重複的快速鍵|
|[CA1302](../code-quality/ca1302.md)|請勿將地區設定特定字串硬式編碼|
|[CA1303](../code-quality/ca1303.md)|不要將常值當作已當地語系化的參數傳遞|
|[CA1304](../code-quality/ca1304.md)|必須指定 CultureInfo|
|[CA1305](../code-quality/ca1305.md)|必須指定 IFormatProvider|
|[CA1306](../code-quality/ca1306.md)|必須設定資料類型的地區設定|
|[CA1307](../code-quality/ca1307.md)|為清楚起見指定 StringComparison|
|[CA1308 必須](../code-quality/ca1308.md)|必須將字串標準化為大寫字母|
|[CA1309](../code-quality/ca1309.md)|使用循序的 StringComparison|
|[CA1310](../code-quality/ca1310.md)|指定 StringComparison 的正確性|
|[CA2101 必須](../code-quality/ca2101.md)|必須指定 P/Invoke 字串引數的封送處理|
