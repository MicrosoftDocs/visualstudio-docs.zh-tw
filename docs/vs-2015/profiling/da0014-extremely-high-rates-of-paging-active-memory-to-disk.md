---
title: DA0014：極高比率的使用中記憶體分頁到磁碟 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba6695b4705a29264f29fa79d23a63062151a62e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730594"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014：極高比率的使用中記憶體分頁到磁碟
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0014 |  
|類別目錄 |記憶體和分頁 |  
|程式碼剖析方法 |所有 |  
|訊息 |發生極高比率的使用中的記憶體分頁到磁碟。 您的應用程式可能是 memory-bound。 |  
|規則類型 |警告 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 25 個樣本才能觸發此規則。  
  
## <a name="cause"></a>原因  
 在分析執行中收集的系統效能資料表示在整個分析執行期間發生極高比率的使用中記憶體分頁進出磁碟。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。 使用更多記憶體在電腦上再次執行分析。  
  
## <a name="rule-description"></a>規則描述  
 過度分頁至磁碟可能是因為實體記憶體不足。 如果分頁作業控制使用分頁檔案所在的實體磁碟，則可能降低相同磁碟上其他應用程式導向之磁碟作業的速度。  
  
 分頁經常以大量分頁作業從磁碟讀取或寫入磁碟。 例如，Pages Output/sec 數經常遠比 Page Writes/sec 數還大。 因為 Pages Output/sec 還包含系統檔案快取的變更資料頁。 不過，不一定可以輕鬆地判斷哪些處理序直接負責分頁或原因。  
  
> [!NOTE]
>  當使用中記憶體的分頁程度達到非常高的比率時，就會引發這個規則。 當分頁程度很高但不是極高時，則會改為引發資訊性規則 [DA0017︰高比率的使用中記憶體分頁到磁碟](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至[標記](../profiling/marks-view.md)檢視。 尋找 **Memory\Pages/sec** 欄。 判斷是否有特定的程式執行階段，當中的分頁 IO 活動比其他階段更繁重。  
  
 如果您在負載測試情節中收集 ASP.NET 應用程式的分析資料，請嘗試在設定額外實體記憶體 (或 RAM) 的機器上再次執行負載測試。  
  
 請考慮修改演算法減少記憶體配置，以及避免需要大量記憶體的 API，例如 String.Concat 和 String.Substring。



