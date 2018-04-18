---
title: 受管理的最小規則規則集為 managed 程式碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6c14af4c569749273b6ed6b73fe48249df3f1ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>受管理的最小規則規則集為 managed 程式碼
Managed 最小規則的重點在於程式碼，包括潛在的安全性漏洞、 應用程式當機，以及其他重要邏輯和設計錯誤中最關鍵的問題。 您應該建立包含這個規則設定任何自訂規則集中您針對您的專案。  
  
|規則|描述|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|應該處置可處置欄位的類型|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的完成項|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|應該處置可處置的欄位|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|多載覆寫 ValueType.Equals 的等號比較運算子|
