---
title: DA0506：為所分析的處理序配置的最大私用位元組 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97d1cacccc2fdd6abbd13aace1de71b28975779e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158052"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506：為所分析的處理序配置的最大私用位元組
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0506 為 |  
|類別目錄 |資源監視 |  
|程式碼剖析方法 |所有 |  
|訊息 |收集這項資訊僅提供資訊。 Process Private Bytes 計數器會測量所分析的處理序配置的虛擬記憶體。 所報告值是所有測量間隔所觀察到最大值。|  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理序目前已配置的虛擬記憶體最大數量，以位元組 (私用位元組) 為單位。 私用位元組表示只能由處理序內執行的執行緒存取的處理序所配置的虛擬記憶體位置。  
  
 對於在 32 位元電腦上執行的 32 位元處理序，處理序位址空間之私用部分的上限是 2 GB。 使用 [/3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini 參數，32 位元處理序就可以取得最大 3 GB 的虛擬記憶體。 在 64 位元電腦上執行的 32 位元處理序可以取得高達 4 GB 的私用虛擬記憶體。  
  
 在 64 位元電腦上執行的 64 位元處理序可以取得高達 8 TB 的私用虛擬記憶體。  
  
 報告的值是所分析的處理序作用中之所有測量間隔的最大值。  
  
 如需處理序位址空間的詳細資訊，請參閱《Windows 記憶體管理》文件中的[虛擬位址空間 (英文)](http://go.microsoft.com/fwlink/?LinkId=177832) 。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用報告的值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。  
  
 處理序私用位元組的最大值，如果接近處理序位址空間可以成長到多大的架構限制，可能會導致記憶體不足的例外狀況。 如需詳細資訊，請參閱 MSDN Magazine 中的[調查記憶體問題 (英文)](http://go.microsoft.com/fwlink/?LinkID=177833)。
