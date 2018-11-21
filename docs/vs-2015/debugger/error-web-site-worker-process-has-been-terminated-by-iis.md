---
title: 錯誤： 網站背景工作處理序已被 IIS 終止 |Microsoft Docs
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
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93271bcba524054a2289b078b0e92fde115eaf23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789053"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>錯誤：網站背景工作處理序已被 IIS 終止
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

偵錯工具停止執行網站上的程式碼。 如此一來，可能會使網際網路資訊服務 (IIS) 認為背景工作處理序已停止回應。 因此，IIS 會結束背景工作處理序。  
  
 若要繼續偵錯，您必須設定 IIS 以允許背景工作處理序繼續進行。 這個錯誤訊息不會出現在 IIS 7 (含) 以前版本中。  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>若要設定 IIS 7 允許背景工作處理序繼續進行  
  
1. 開啟**系統管理工具**視窗。  
  
   1.  按一下 **開始**，然後選擇**控制台**。  
  
   2.  在**控制台中**，選擇**切換至傳統檢視**，如有必要，然後按兩下**系統管理工具**。  
  
2. 在 [**系統管理工具**] 視窗中，按兩下**Internet Information Services (IIS) 管理員**。  
  
    [IIS 管理員] 隨即開啟。  
  
3. 在 **連線**窗格中，展開\<電腦名稱 > 如有必要的節點。  
  
4. 底下\<電腦名稱 > 節點，按一下**應用程式集區**。  
  
5. 在 **應用程式集區**清單中，以滑鼠右鍵按一下 集區中，執行應用程式的名稱，然後按一下**進階設定**。  
  
6. 在 [**進階設定]** 對話方塊方塊中，找出**處理序模型**區段，然後執行下列動作之一：  
  
   - 設定**已啟用 Ping**要**False**。  
  
   - 設定**Ping 回應時間上限**大於 90 秒的值。  
  
     設定**已啟用 Ping**要**False** IIS 停止檢查背景工作處理序是否仍在執行，並讓背景工作處理序保持運作，直到您停止您偵錯的處理序。 設定**Ping 回應時間上限**大的值可讓 IIS 繼續監視背景工作處理序。  
  
7. 按一下 [ **[確定]** 以關閉**進階設定**] 對話方塊。  
  
8. 關閉 IIS 管理員和**系統管理工具**視窗。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)



