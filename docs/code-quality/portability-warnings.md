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
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163077"
---
# <a name="portability-warnings"></a>可攜性警告
可攜性警告支援跨不同作業系統的可攜性。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1900：實數值型別欄位應該是可移植的 @ no__t-0|此規則會檢查使用明確版面配置屬性所宣告的結構，在64位作業系統上封送處理至非受控碼時，會正確對齊。|
|[CA1901：P/Invoke 宣告應該是可移植的 @ no__t-0|此規則會評估每個參數的大小和 P/Invoke 的傳回值，並在32位和64位作業系統上封送處理至未受管理的程式碼時，確認其大小是否正確。|
|[CA1903：僅使用來自目標架構的 API @ no__t-0|某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。|
