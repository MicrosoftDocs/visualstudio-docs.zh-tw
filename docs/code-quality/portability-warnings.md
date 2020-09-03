---
title: Portability Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "78167569"
---
# <a name="portability-warnings"></a>Portability Warnings
可攜性警告支援不同作業系統之間的可攜性。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1900:實值類型欄位應該為可移植的](../code-quality/ca1900.md)|這項規則會檢查在64位作業系統上封送處理至非受控碼時，使用明確配置屬性所宣告的結構是否會正確對齊。|
|[CA1901： P/Invoke 宣告應該是可移植的](../code-quality/ca1901.md)|這項規則會評估每個參數的大小和 P/Invoke 的傳回值，並在32位和64位作業系統上封送處理至非受控碼時，確認其大小是否正確。|
|[CA1903:只使用來自目標架構的 API](../code-quality/ca1903.md)|某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。|
