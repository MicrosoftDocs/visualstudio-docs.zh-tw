---
title: DA0029：不支援的 CLR 版本 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3855b8975684b088b2838a866db36e6ec19e665
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635536"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029：不支援的 CLR 版本

|||
|-|-|
|規則 ID|DA0029|
|分類|分析工具使用方式|
|程式碼剖析方法|從命令列進行程式碼剖析|
|訊息|在收集期間偵測到不支援的 CLR 版本。 可能無法正確解析 Managed 符號。|
|規則型別|資訊。|

## <a name="cause"></a>原因
 您嘗試使用分析工具不支援的 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] 來分析應用程式。

## <a name="rule-description"></a>規則描述
 因為分析工具無法解析應用程式中執行之 Managed 程式碼的符號，所以發生此警告。 分析工具無法解析執行 [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] 之應用程式的受控碼符號。

## <a name="how-to-fix-violations"></a>如何修正違規
 無。