---
title: 受管理的最小規則規則集為 managed 程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f67b9e28069a1717ad500b7e8895a363db715fda
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251056"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的 Managed 最小規則規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

受管理的最小規則著重於包括潛在的安全性漏洞、 應用程式當機，以及其他重要的邏輯和設計錯誤的程式碼中最關鍵的問題。 您應該包含您專案建立的此規則設定任何自訂規則集中。  
  
|規則|描述|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|可處置欄位的類型應該是可處置的|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的完成項|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|多載覆寫 ValueType.Equals 的等號比較運算子|



