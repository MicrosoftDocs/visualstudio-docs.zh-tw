---
title: DA0003：許多核心樣本 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 69cd81943641e4e0585a67127c70d35a601a5396
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777734"
---
# <a name="da0003-many-kernel-samples"></a>DA0003：許多核心樣本

|||
|-|-|
|規則 ID|DA0003|
|類別|分析工具使用方式|
|分析方法|取樣|
|訊息|您在核心模式中有高比例的樣本。 這可能指出大量 I/O 活動或較高的內容切換率。 請考慮使用檢測模式重新分析應用程式。|
|規則型別|資訊|

## <a name="cause"></a>原因
 針對應用程式收集的大部分呼叫堆疊範例是以核心模式執行。 請考慮使用不同的分析方法來分析應用程式。

## <a name="rule-description"></a>規則描述
 在 Windows 中，您可以使用核心模式或使用者模式來執行程式碼  （核心模式也稱為特權模式。只有低級系統代碼（如裝置驅動程式）在核心模式下運行。 使用者模式應用程式可以轉換為核心模式以執行 I/O 作業、等候執行緒或處理序同步原始物件，或執行系統呼叫。

 當您要分析將大部分時間都用在以使用者模式工作的分析應用程式時，取樣最為有效。 以核心模式執行應用程式時所收集的樣本數目可能指出經常執行的 I/O 作業，或可能指出正在發生內容參數。 無法使用取樣方法來調查其中任一項作業。 如果取得太多核心模式樣本，則取樣資料可能未包含足夠的使用者模式樣本來進行統計。

## <a name="how-to-fix-violations"></a>如何修正違規
 請考慮使用下列其中一個選項重新分析應用程式：

- 使用檢測方法進行分析。

- 增加取樣率，嘗試以使用者模式收集更多的樣本。
