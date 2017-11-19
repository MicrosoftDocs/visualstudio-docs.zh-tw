---
title: "如何： 自我裝載的 WCF 服務進行偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e64f764153106c252ba1a9586bfd0a33f4e239f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>如何：偵錯自我裝載的 WCF 服務
A*自我裝載的服務*是在 IIS、 WCF 服務主機，不會執行的 WCF 服務或[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]程式開發伺服器。 若要偵錯自我裝載的 WCF 的最簡單方式是設定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]啟動用戶端和伺服器，當您選擇**開始偵錯**上**偵錯**功能表。  
  
 如果 WCF 服務自我裝載內部或程序無法啟動，請在這種方式，例如 NT 服務，您無法使用這個方法。 相反地，您可以執行下列其中一項：  
  
-   以手動方式將偵錯工具附加至裝載的處理序。 如需詳細資訊，請參閱[附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
     — 或 —  
  
-   開始偵錯用戶端，並接著逐步執行服務的呼叫。 這需要您啟用的 app.config 檔案中的偵錯。 如需詳細資訊， [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>若要從 Visual Studio 啟動用戶端和主機  
  
1.  建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包含用戶端和伺服器專案的方案。  
  
2.  設定解決方案來啟動用戶端和伺服器處理序，當您選擇**啟動**上**偵錯**功能表。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下方案名稱。  
  
    2.  按一下**設定啟始專案**。  
  
    3.  在**方案\<名稱 > 屬性**對話方塊中，選取**多個啟始專案**。  
  
    4.  在**多個啟始專案**方格中的，對應至伺服器專案中，在列上按一下**動作**選擇**啟動**。  
  
    5.  在一行中對應至用戶端專案，按一下 **動作**選擇**啟動**。  
  
    6.  按一下 [確定]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)   
 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：逐步執行 WCF 服務](../debugger/how-to-step-into-wcf-services.md)