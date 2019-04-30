---
title: 可攜性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a3557cffec60de91da46f60040ec675c866cbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825321"
---
# <a name="portability-warnings"></a>可攜性警告
支援跨不同的作業系統可攜性警告的可攜性。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1900： 實實值類型欄位應該為可移植的](../code-quality/ca1900-value-type-fields-should-be-portable.md)|此規則會檢查封送處理至 unmanaged 程式碼，在 64 位元作業系統上時使用明確的配置屬性宣告的結構會正確地對齊。|
|[CA1901:P/Invoke 宣告應該為可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|此規則會評估每個參數的大小和 P/Invoke，傳回值，並驗證它們的大小正確封送處理至 unmanaged 程式碼在 32 位元和 64 位元作業系統上時。|
|[CA1903:使用來自目標架構的 API](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。|