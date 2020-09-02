---
title: FxCopCmd 錯誤 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787282"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd 錯誤
FxCopCmd 不會將所有錯誤視為嚴重錯誤。 如果 FxCopCmd 有足夠的資訊來執行部分分析，它就會執行分析並報告發生的錯誤。 錯誤碼（32位整數）包含對應至錯誤之數值的位元組合。  
  
 下表說明 FxCopCmd 傳回的錯誤碼：  
  
|錯誤|數值|  
|-----------|-------------------|  
|沒有錯誤|0x0|  
|分析錯誤|0x1|  
|規則例外|0x2|  
|專案載入錯誤|0x4|  
|元件載入錯誤|0x8|  
|規則程式庫載入錯誤|0x10|  
|匯入報表載入錯誤|0x20|  
|輸出錯誤|0x40|  
|命令列參數錯誤|0x80|  
|初始化錯誤|0x100|  
|元件參考錯誤|0x200|  
|BuildBreakingMessage|0x400|  
|未知的錯誤|0x1000000|  
  
 發生嚴重錯誤時，會傳回分析錯誤。 指出無法完成分析。 在適用的情況下，錯誤碼也包含嚴重錯誤的根本原因。 下列條件會產生嚴重錯誤：  
  
- 無法執行分析，因為輸入不足。  
  
- 分析擲回了 FxCopCmd 未處理的例外狀況。  
  
- 找不到指定的專案檔或已損毀。  
  
- 未指定輸出選項，或無法寫入檔案。  
  
    > [!NOTE]
    > FxCopCmd 傳回碼「元件參考錯誤」本身的0x200 本身是警告，而非錯誤。 這個傳回碼表示發現遺漏的間接參考，但 FxCopCmd 能夠處理它們。 有可能是某些分析結果可能已遭入侵的警告。 當與任何其他傳回碼合併時，請考慮「元件參考錯誤」傳回碼為錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)