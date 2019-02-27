---
title: DA0008：只收集到少量樣本 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b33193f30edd19ef18ead5cf15f2e41d352f4d4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630375"
---
# <a name="da0008-few-samples-collected"></a>DA0008：只收集到少量樣本

|||
|-|-|
|規則 ID|DA0008|
|分類|分析工具使用方式|
|程式碼剖析方法|取樣|
|訊息|只收集到少量樣本。 請考慮執行較長時間或較快速的取樣率，以取得較大量的結果。|
|規則型別|資訊|

## <a name="cause"></a>原因
 在執行分析中只收集到少量樣本。

## <a name="rule-description"></a>規則描述
 使用取樣方法時，您應該收集統計顯著的樣本數目，以確保資料代表實際的程式行為。 若要讓取樣錯誤降到最少，您應該嘗試至少收集 1000個程式指令執行行為的樣本。 如果您沒有收集到足夠的樣本，對分析資料進行分析時，可能會被誤導。

## <a name="how-to-fix-violations"></a>如何修正違規
 請考慮分析較長的應用程式執行時間，或使用更快速的取樣率來取得統計顯著的結果。 如需如何在 Visual Studio IDE 中變更取樣速率的資訊，請參閱[如何：選擇取樣事件](../profiling/how-to-choose-sampling-events.md)。 如需如何使用分析工具命令列變更取樣率的詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 參考中的[計時器](../profiling/timer.md)。