---
title: DA0505-配置給所分析進程的平均私用位元組 |Microsoft 檔
description: 此訊息報告處理序目前已配置的虛擬記憶體平均數量，以位元組 (私用位元組) 為單位。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f141ce40c22fbd6ee9445dc676b49f0d601f2a74
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465812"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505：為所分析處理序配置的平均私用位元組

|Item|值|
|-|-|
|規則 ID|DA0505|
|類別|資源管理|
|程式碼剖析方法|全部|
|訊息|收集此資訊僅供參考之用。 Process Private Bytes 計數器會測量所分析的處理序配置的虛擬記憶體。 報告的值是針對所有測量間隔計算的平均。|
|規則型別|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="rule-description"></a>規則描述
 此訊息報告處理序目前已配置的虛擬記憶體平均數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。

 對於在 32 位元電腦上執行的 32 位元處理序，處理序位址空間之私用部分的上限是 2 GB。 使用 [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini 參數，32 位元處理序就可以取得最大 3 GB 的虛擬記憶體。 在 64 位元電腦上執行的 32 位元處理序可以取得高達 4 GB 的私用虛擬記憶體。

 在 64 位元電腦上執行的 64 位元處理序可以取得高達 8 TB 的私用虛擬記憶體。

 報告的值是所分析的處理序作用中之所有測量間隔的平均。

 如需處理序位址空間的詳細資訊，請參閱《Windows 記憶體管理》文件中的[虛擬位址空間 (英文)](/windows/win32/memory/virtual-address-space) 。

## <a name="how-to-use-rule-data"></a>如何使用規則資料
 使用報告的值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。
