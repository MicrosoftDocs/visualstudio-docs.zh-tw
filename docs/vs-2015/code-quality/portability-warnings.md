---
title: 可攜性警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671160"
---
# <a name="portability-warnings"></a>Portability Warnings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

可攜性警告支援不同作業系統之間的可攜性。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1900:實值類型欄位應該為可移植的](../code-quality/ca1900-value-type-fields-should-be-portable.md)|這項規則會檢查在64位作業系統上封送處理至非受控碼時，使用明確配置屬性所宣告的結構是否會正確對齊。|
|[CA1901： P/Invoke 宣告應該是可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|這項規則會評估每個參數的大小和 P/Invoke 的傳回值，並在32位和64位作業系統上封送處理至非受控碼時，確認其大小是否正確。|
|[CA1903:只使用來自目標架構的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。|
