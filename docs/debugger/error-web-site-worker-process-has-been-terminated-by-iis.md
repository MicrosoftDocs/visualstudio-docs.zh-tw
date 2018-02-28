---
title: "錯誤： 網站背景工作處理序已被 IIS 終止 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fb7a0220cf6650aeeb12ec6549d112a39918de3f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>錯誤：網站背景工作處理序已被 IIS 終止
偵錯工具停止執行網站上的程式碼。 如此一來，可能會使網際網路資訊服務 (IIS) 認為背景工作處理序已停止回應。 因此，IIS 會結束背景工作處理序。  
  
 若要繼續偵錯，您必須設定 IIS 以允許背景工作處理序繼續進行。 這個錯誤訊息不會出現在 IIS 7 (含) 以前版本中。  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>若要設定 IIS 7 允許背景工作處理序繼續進行  
  
1.  開啟**系統管理工具**視窗。  
  
    1.  按一下**啟動**，然後選擇 **控制台**。  
  
    2.  在**控制台**，選擇**切換到傳統檢視**，如有必要，然後按兩下**系統管理工具**。  
  
2.  在**系統管理工具**視窗中，按兩下**網際網路資訊服務 (IIS) 管理員**。  
  
     [IIS 管理員] 隨即開啟。  
  
3.  在**連線**] 窗格中，展開 [\<電腦名稱 > 節點，如有必要。  
  
4.  在下\<電腦名稱 >] 節點，按一下 [**應用程式集區**。  
  
5.  在**應用程式集區**清單中，以滑鼠右鍵按一下 集區中，執行應用程式的名稱，然後按一下 **進階設定**。  
  
6.  在**進階設定**對話方塊方塊中，找出**處理序模型**區段，並執行下列動作之一：  
  
    -   設定**已啟用 Ping**至**False**。  
  
    -   設定**Ping 回應時間上限**大於 90 秒的值。  
  
     設定**已啟用 Ping**至**False** IIS 停止檢查背景工作處理序是否仍在執行，並保持背景工作處理序運作，直到您停止您偵錯的處理序。 設定**Ping 回應時間上限**較大的值可讓 IIS 繼續監視背景工作處理序。  
  
7.  按一下**確定**關閉**進階設定** 對話方塊。  
  
8.  關閉 IIS 管理員和**系統管理工具**視窗。  
  
## <a name="see-also"></a>請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)