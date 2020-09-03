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
ms.openlocfilehash: 69a7eaeecd65ffdfbd575b59fbea15c476d0fbeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850872"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505：為所分析處理序配置的平均私用位元組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則識別碼 |DA0505 |  
|類別 |資源管理 |  
|分析方法 |全部 |  
|訊息 |此資訊只會針對資訊收集。 Process Private Bytes 計數器會測量所分析的處理序配置的虛擬記憶體。 所報告值是針對所有測量間隔計算的平均值。|  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理序目前已配置的虛擬記憶體平均數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。  
  
 對於在 32 位元電腦上執行的 32 位元處理序，處理序位址空間之私用部分的上限是 2 GB。 使用 [/3GB](https://msdn.microsoft.com/library/ff556232.aspx) Boot.ini 參數，32 位元處理序就可以取得最大 3 GB 的虛擬記憶體。 在 64 位元電腦上執行的 32 位元處理序可以取得高達 4 GB 的私用虛擬記憶體。  
  
 在 64 位元電腦上執行的 64 位元處理序可以取得高達 8 TB 的私用虛擬記憶體。  
  
 報告的值是所分析的處理序作用中之所有測量間隔的平均。  
  
 如需處理序位址空間的詳細資訊，請參閱《Windows 記憶體管理》文件中的[虛擬位址空間 (英文)](https://msdn.microsoft.com/library/aa366912.aspx) 。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用報告的值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。
