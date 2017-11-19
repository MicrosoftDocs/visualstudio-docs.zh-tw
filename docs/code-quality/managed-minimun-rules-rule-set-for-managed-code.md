---
title: "受管理的最小規則規則集為 managed 程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac5ec4db1fe36d7e92c4f9062f8d0c28bae2263e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>受管理的最小規則規則集為 managed 程式碼
Managed 最小規則的重點在於程式碼，包括潛在的安全性漏洞、 應用程式當機，以及其他重要邏輯和設計錯誤中最關鍵的問題。 您應該建立包含這個規則設定任何自訂規則集中您針對您的專案。  
  
|規則|說明|  
|----------|-----------------|  
|[CA1001 具有](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|應該處置可處置欄位的類型|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的完成項|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|應該處置可處置的欄位|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|多載覆寫 ValueType.Equals 的等號比較運算子|
