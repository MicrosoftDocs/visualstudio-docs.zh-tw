---
title: "偵錯已部署的 ASP.NET 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/30/2017
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
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 421c1f5f8736b9bd2cd95ac61570cc831c468c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-deployed-aspnet-applications"></a>偵錯已部署的 ASP.NET 應用程式
若要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯已部署的應用程式，您必須附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序，並且確定偵錯工具可以存取應用程式的符號。 您還必須找出並開啟應用程式的原始程式檔 (Source File)。 如需詳細資訊，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)，[如何： 尋找 ASP.NET 處理序名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)，和[系統需求](../debugger/aspnet-debugging-system-requirements.md)。  

> [!WARNING]
> 如果您附加到[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]背景工作處理序偵錯和叫用中斷點時，所有受管理的程式碼中背景工作處理序會中止。 中止背景工作處理序中所有 Managed 程式碼可能會使伺服器上所有使用者的作業停止。 在實際執行伺服器上偵錯之前，請務必考慮對實際執行工作的可能影響。 
  
用來附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的處理序，和附加至其他任何遠端處理序一樣。 當您附加之後，如果您沒有開啟正確的專案時，對話方塊隨即出現在應用程式中斷時。 這個對話方塊會要求您輸入應用程式原始程式檔的位置。 您在對話方塊中所指定的檔名，必須符合偵錯符號 (位於 Web 伺服器上) 中指定的檔名。 如需詳細資訊，請參閱[附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。 若要設定在 IIS 上的遠端偵錯，請參閱[遠端 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。
 
> [!NOTE]
>  許多 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式都會參考到包含商務邏輯或其他實用程式碼的 DLL。 這類的參考將 DLL 複製從本機電腦的 Web 應用程式的虛擬目錄的 \bin 資料夾時部署您的應用程式。 在偵錯時請記住，您的 Web 應用程式是參考該 DLL 的複本而非本機電腦上的複本。 
  
## <a name="see-also"></a>另請參閱  
 [偵錯 ASP.NET 應用程式](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何： 啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [如何： 尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)