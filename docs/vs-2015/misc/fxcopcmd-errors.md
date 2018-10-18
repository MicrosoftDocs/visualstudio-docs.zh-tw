---
title: FxCopCmd 錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: susanno
manager: douge
ms.openlocfilehash: eae6b19d9901eb2a2d047b4c262b02a825c0f83b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303208"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd 錯誤
FxCopCmd 不會考慮所有的錯誤，是嚴重的錯誤。 如果 FxCopCmd 有足夠的資訊來執行部分的分析，它會執行分析和報告所發生的錯誤。 錯誤的程式碼，也就是 32 位元整數，包含對應至錯誤的數字值的位元組合。  
  
 下表描述 FxCopCmd 所傳回的錯誤碼：  
  
|錯誤|數字值|  
|-----------|-------------------|  
|沒有錯誤|0x0|  
|分析錯誤|0x1|  
|規則的例外狀況|0x2|  
|專案載入錯誤|0x4|  
|組件載入錯誤|0x8|  
|規則文件庫載入錯誤|0x10|  
|匯入報表載入錯誤|0x20|  
|輸出錯誤|0x40|  
|命令列參數錯誤|0x80|  
|初始化錯誤|0x100|  
|組件參考錯誤|0x200|  
|BuildBreakingMessage|0x400|  
|未知的錯誤|0x1000000|  
  
 分析錯誤會傳回嚴重錯誤。 表示無法完成分析。 適用時，錯誤程式碼也會包含嚴重錯誤的根本原因。 在下列情況會產生嚴重的錯誤：  
  
-   分析無法執行輸入不足所造成。  
  
-   分析會擲回 FxCopCmd 未處理的例外狀況。  
  
-   找不到指定的專案檔，或已損毀。  
  
-   未指定輸出選項，或無法寫入檔案。  
  
    > [!NOTE]
    >  FxCopCmd 傳回碼 「 組件參考錯誤 」 0x200 本身是警告，而不是錯誤。 此傳回碼指出遺漏的間接參考找不到，但 FxCopCmd 無法處理它們。 它會警告是，某些分析結果可能被盜用的可能性。 它結合任何其他傳回碼時，則您可以視為錯誤 「 組件參考錯誤 」 的傳回碼。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)