---
title: Managed 程式碼的 managed 最小規則規則集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83f8654a3cca246fa4853add231008e2fadbfc1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667905"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的 Managed 最小規則規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

受管理的最小規則會著重于程式碼中最嚴重的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 您應該在為專案建立的任何自訂規則集中包含此規則集。

|規則|描述|
|----------|-----------------|
|[CA1001 具有](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可處置欄位的類型應該為可處置|
|[CA1821 必須](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|在覆寫 ValueType.Equals 上多載等號運算子|
