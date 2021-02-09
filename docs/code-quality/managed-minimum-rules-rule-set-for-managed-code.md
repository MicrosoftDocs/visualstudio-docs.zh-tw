---
title: 適用於受控碼的受控最小規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中的 Managed 最小規則規則集，其中著重于安全性、穩定性和其他重大問題。 請參閱規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8711fd0a265618a5aaf4f84edcf7dd2b081b16a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859810"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>適用於受控碼的受控最小規則規則集

受管理的最小規則會著重于程式碼中最嚴重的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 在您為專案建立的任何自訂規則集中包含此規則集。

|規則|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|具有可處置欄位的類型應該為可處置|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|必須移除空的完成項|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|可處置的欄位應該受到處置|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|覆寫上的多載運算子 equals `ValueType.Equals`|
