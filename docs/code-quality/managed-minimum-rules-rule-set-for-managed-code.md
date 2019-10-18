---
title: 適用於受控碼的受控最小規則規則集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 10758bbabeb21f00ea10dd779bc6a44acdcc6bba
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535784"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>適用於受控碼的受控最小規則規則集

受管理的最小規則會專注于程式碼中最嚴重的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 將此規則集包含在您為專案建立的任何自訂規則集中。

|規則|描述|
|----------|-----------------|
|[CA1001 具有](../code-quality/ca1001.md)|具有可處置欄位的類型應該為可處置|
|[CA1821 必須](../code-quality/ca1821.md)|必須移除空的完成項|
|[CA2213](../code-quality/ca2213.md)|可處置的欄位應該受到處置|
|[CA2231](../code-quality/ca2231.md)|在覆寫時，多載運算子 equals `ValueType.Equals`|
