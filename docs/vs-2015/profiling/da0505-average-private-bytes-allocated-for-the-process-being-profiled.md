---
title: DA0505：為所分析的處理序配置的平均私用位元組 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fde4228538a26a4601dc7eb5638a4b803dafbacb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793044"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505：為進行程式碼剖析的處理序所配置的平均私用位元組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0505 為 |  
|類別目錄 |資源管理 |  
|程式碼剖析方法 |所有 |  
|訊息 |收集這項資訊僅提供資訊。 Process Private Bytes 計數器會測量所分析的處理序配置的虛擬記憶體。 所報告值是針對所有測量間隔計算的平均值。|  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理序目前已配置的虛擬記憶體平均數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。  
  
 對於在 32 位元電腦上執行的 32 位元處理序，處理序位址空間之私用部分的上限是 2 GB。 使用 [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini 參數，32 位元處理序就可以取得最大 3 GB 的虛擬記憶體。 在 64 位元電腦上執行的 32 位元處理序可以取得高達 4 GB 的私用虛擬記憶體。  
  
 在 64 位元電腦上執行的 64 位元處理序可以取得高達 8 TB 的私用虛擬記憶體。  
  
 報告的值是所分析的處理序作用中之所有測量間隔的平均。  
  
 如需處理序位址空間的詳細資訊，請參閱《Windows 記憶體管理》文件中的[虛擬位址空間 (英文)](http://go.microsoft.com/fwlink/?LinkId=177832) 。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用報告的值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。
