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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8f195f2219cfa2c81b24a3e04ddc559dc98a06
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942696"
---
# <a name="portability-warnings"></a>可攜性警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

支援跨不同的作業系統可攜性警告的可攜性。  
  
## <a name="in-this-section"></a>本節內容  
  
|規則|描述|  
|----------|-----------------|  
|[CA1900： 實實值類型欄位應該為可移植的](../code-quality/ca1900-value-type-fields-should-be-portable.md)|此規則會檢查封送處理至 unmanaged 程式碼，在 64 位元作業系統上時使用明確的配置屬性宣告的結構會正確地對齊。|  
|[CA1901:P/Invoke 宣告應該為可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|此規則會評估每個參數的大小和 P/Invoke，傳回值，並驗證它們的大小正確封送處理至 unmanaged 程式碼在 32 位元和 64 位元作業系統上時。|  
|[CA1903:使用來自目標架構的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。|
