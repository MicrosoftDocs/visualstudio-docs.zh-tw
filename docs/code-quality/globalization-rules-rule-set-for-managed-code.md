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
ms.openlocfilehash: 2af6126c751d03968dc7ecd87693e3546376c12a
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509857"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的全球化規則規則集

使用 Microsoft 全球化規則規則集，將焦點放在可能導致應用程式中的資料無法在不同語言、地區設定和文化特性中正確顯示的問題。 如果您的應用程式已當地語系化、全球化或兩者皆是，則應包含此規則集。

|規則|描述|
|----------|-----------------|
|[CA1303](../code-quality/ca1303.md)|不要將常值當作已當地語系化的參數傳遞|
|[CA1304](../code-quality/ca1304.md)|必須指定 CultureInfo|
|[CA1305](../code-quality/ca1305.md)|必須指定 IFormatProvider|
|[CA1307](../code-quality/ca1307.md)|為清楚起見指定 StringComparison|
|[CA1308 必須](../code-quality/ca1308.md)|必須將字串標準化為大寫字母|
|[CA1309](../code-quality/ca1309.md)|使用循序的 StringComparison|
|[CA1310](../code-quality/ca1310.md)|指定 StringComparison 的正確性|
|[CA2101 必須](../code-quality/ca2101.md)|必須指定 P/Invoke 字串引數的封送處理|
