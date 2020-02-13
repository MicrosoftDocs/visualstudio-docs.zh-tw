---
title: DA0503：所分析之處理序的平均工作集 (以位元組為單位) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 31d36a89473cd0c6a0b55e484fee2ce1d7045b15
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850887"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503：進行程式碼剖析之處理序的平均工作集 (以位元組為單位)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則識別碼 |DA0503 |  
|類別 |資源監視 |  
|程式碼剖析方法 |全部 |  
|訊息 |這只是收集資訊的資訊。 「處理序工作集」計數器會依您分析的處理序測量實體記憶體的使用方式。 所報告值是針對所有測量間隔計算的平均值。|  
|規則類型 |資訊 |  
  
 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。  
  
## <a name="rule-description"></a>規則描述  
 此訊息報告處理序目前使用的實體記憶體平均數量，以位元組 (工作集) 為單位。 處理序工作集表示目前位於實體記憶體中之處理序位址空間的頁面。  
  
 報告的值包含處理序參考之共用記憶體區段的固有頁面。 處理序參考的共用 DLL 包含在計算的共用記憶體區段中。 處理序工作集的值可以高於處理序因為共用記憶體區段而配置的虛擬記憶體數量。  
  
 報告的值是所分析的處理序作用中之所有測量間隔的平均。  
  
 處理序工作集大小會反映處理序正在使用多少虛擬記憶體。 它也會受到執行應用程式可用的實體記憶體 (或 RAM) 數量，以及其他執行中處理序對該實體記憶體的爭用的影響。 如果實體記憶體受到限制，當作業系統定期修剪處理序工作集中完全非作用中的頁面以嘗試平衡作用中處理序之間的記憶體使用量時，處理序工作集的值就很容易大幅變化。  
  
 如需處理序工作集的詳細資訊，請參閱 MSDN 網站上＜Windows 記憶體管理＞文件中的[工作集](https://msdn.microsoft.com/library/cc441804.aspx)。  
  
## <a name="how-to-use-rule-data"></a>如何使用規則資料  
 使用規則值可比較程式不同版本或組建的效能，或了解不同分析情節中的應用程式效能。  
  
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至分析資料的[標記檢視](../profiling/marks-view.md)。 尋找 **Process\Working Set** 和 **Memory\Pages/sec** 欄。 比較兩欄，判斷是否有特定的程式執行階段看起來似乎與分頁 IO 活動增加有關。
