---
title: 適用於 Managed 程式碼的全球化規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中的全球化規則規則集，其中著重于與語言、地區設定和文化特性相關的問題。 請參閱規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0bf96c8e4140e5b491624d6750b498a26726761c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348875"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的全球化規則規則集

使用 Microsoft 全球化規則規則集，將焦點放在可能導致應用程式中的資料無法在不同語言、地區設定和文化特性中正確顯示的問題。 如果您的應用程式已當地語系化、全球化或兩者皆是，則應包含此規則集。

|規則|說明|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|不要將常值當作已當地語系化的參數傳遞|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|必須指定 CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|必須指定 IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|為清楚起見指定 StringComparison|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|必須將字串標準化為大寫字母|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|使用循序的 StringComparison|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|指定 StringComparison 的正確性|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|必須指定 P/Invoke 字串引數的封送處理|
