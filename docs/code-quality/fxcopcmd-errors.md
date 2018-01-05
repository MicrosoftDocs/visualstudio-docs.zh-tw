---
title: "FxCopCmd 錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 48b082f5b00f260d2f8e2519a4551fab23dc1011
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd 錯誤
FxCopCmd 不會考慮所有是嚴重的錯誤。 如果 FxCopCmd 有足夠的資訊來執行部分的分析，它會執行分析及報告所發生錯誤。 錯誤的程式碼，也就是 32 位元整數，包含對應至錯誤的數字值的位元組合。  
  
 下表描述 FxCopCmd 所傳回的錯誤碼：  
  
|錯誤|數值|  
|-----------|-------------------|  
|沒有錯誤|0x0|  
|分析錯誤|0x1|  
|規則例外狀況|0x2|  
|專案載入錯誤|0x4|  
|組件載入錯誤|0x8|  
|規則的程式庫載入錯誤|0x10|  
|匯入報表載入錯誤|0x20|  
|輸出錯誤|0x40|  
|命令列參數錯誤|0x80|  
|初始化錯誤|0x100|  
|組件參考錯誤|0x200|  
|BuildBreakingMessage|0x400|  
|未知的錯誤|0x1000000|  
  
 分析錯誤會傳回嚴重錯誤。 表示無法完成分析。 當適用時，錯誤程式碼也包含嚴重錯誤的根本原因。 下列情況會產生嚴重的錯誤：  
  
-   分析可能不會執行輸入不足所造成。  
  
-   分析擲回不由 FxCopCmd 處理的例外狀況。  
  
-   找不到指定的專案檔，或已損毀。  
  
-   未指定輸出選項，或無法寫入檔案。  
  
    > [!NOTE]
    >  FxCopCmd 傳回碼 「 組件參考錯誤 」 0x200 本身是警告，而不是錯誤。 此傳回碼表示找到遺失的間接參考，但 FxCopCmd 無法處理它們。 是，某些分析結果可能已經洩漏可能發生的警告。 它結合任何其他傳回碼時，請考慮為錯誤的 「 組件參考錯誤 」 的傳回碼。  
  
## <a name="see-also"></a>請參閱  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)