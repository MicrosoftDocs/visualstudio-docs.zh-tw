---
title: 受管理的最小規則規則集為 managed 程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fbbbdf8a1ece9a57d0216a6c9b59ac9d2a8ea474
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142222"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的 Managed 最小規則規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

受管理的最小規則著重於包括潛在的安全性漏洞、 應用程式當機，以及其他重要的邏輯和設計錯誤的程式碼中最關鍵的問題。 您應該包含您專案建立的此規則設定任何自訂規則集中。  
  
|規則|描述|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可處置欄位的類型應該為可處置|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|在覆寫 ValueType.Equals 上多載等號運算子|
