---
title: DA0504-所分析之進程的最大工作集（以位元組為單位） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c218965add570035e9396652cec46279fcebc4d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931743"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504：所分析之處理序的最大工作集 (以位元組為單位)

|Item|值|
|-|-|
|規則 ID|DA0504|
|類別|資源管理|
|程式碼剖析方法|全部|
|訊息|收集此資訊僅供參考之用。 「處理序工作集」計數器會依您分析的處理序測量實體記憶體的使用方式。 報告的值是所有測量間隔所觀察到最大值。|
|規則型別|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="rule-description"></a>規則描述
 此訊息報告處理序目前使用的實體記憶體最大數量，以位元組為單位。 處理序工作集表示目前位於實體記憶體中之處理序位址空間的頁面。 此規則回報分析進行時，處理序工作集的最大值。

 報告的值包含處理序參考之共用記憶體區段的固有頁面。 處理序參考的共用 DLL 包含在計算的共用記憶體區段中。 處理序工作集的值可以高於處理序因為共用記憶體區段而配置的虛擬記憶體數量。

 處理序工作集大小會反映處理序正在使用多少虛擬記憶體。 它也會受到執行應用程式可用的實體記憶體 (或 RAM) 數量，以及其他執行中處理序對該實體記憶體的爭用的影響。 如需處理序工作集的詳細資訊，請參閱 MSDN 網站上＜Windows 記憶體管理＞文件中的[工作集](/windows/win32/memory/working-set)。

## <a name="how-to-use-rule-data"></a>如何使用規則資料
 此規則會從 Windows 效能監視功能收集這個測量資料，但只報告做為參考資訊。 使用此資料可比較程式不同版本或組建的效能，或了解不同測試情節中的應用程式效能。

 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至分析資料的[標記檢視](../profiling/marks-view.md)。 尋找 **Process\Working Set** 和 **Memory\Pages/sec** 計數器欄。 然後找出 **Process\Working Set** 的最大值並與 **Memory\Pages/sec** 值比較。 工作集最大值通常與分頁 IO 活動減少的間隔相關，如果機器的記憶體受到限制時尤其如此。
