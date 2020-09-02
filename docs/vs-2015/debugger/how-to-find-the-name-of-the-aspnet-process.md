---
title: 如何：尋找 ASP.NET 流程的名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685948"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>如何：尋找 ASP.NET 處理序的名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要附加至執行中的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式，您必須知道 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 處理序的名稱：  
  
- 如果您執行的是 IIS 6.0 或 IIS 7.0，則名稱是 w3wp.exe。  
  
- 如果您執行的是 IIS 的先前版本，則名稱是 aspnet_wp.exe。  
  
  針對使用或更新版本所建立的應用程式 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] ，程式 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 代碼可位於檔案系統上，並在測試伺服器 WebDev.WebServer.exe 下執行。 在此情況下，您需要附加至 WebDev.WebServer.exe，而非 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 處理序。 本案例僅適用於本機偵錯。  
  
  舊版 ASP 應用程式會在它們以同處理序 (In-Process) 方式執行時，於 IIS 處理序 inetinfo.exe 中執行。  
  
> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>若要判斷專案程式碼是位於檔案系統或 IIS 上  
  
1. 在 Visual Studio 中，開啟 **方案總管** （如果尚未開啟）。  
  
2. 選取包含應用程式名稱的最上層節點。  
  
3. 如果 [ **屬性** ] 視窗標題包含檔案路徑，則應用程式程式碼會位於檔案系統上。  
  
     否則，[ **屬性** ] 視窗標題將包含網站的名稱。  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>若要判斷應用程式在哪一個 IIS 版本下執行  
  
1. 尋找系統 **管理工具** 並加以執行。 視您的作業系統而定，這可能是 **主控台**中的圖示，或是當您按一下 [ **開始**] 時出現的功能表項目。  
  
     在 Windows XP 中， **主控台** 可以在類別目錄檢視或傳統視圖中。 在類別目錄檢視中，您必須按一下 [ **切換到傳統視圖** ] 或 [ **效能及維護** ]，以查看 [系統 **管理工具** ] 圖示。  
  
2. 從 [系統 **管理工具**] 中，執行 Internet Information Services。 MMC 對話方塊就會出現。  
  
3. 如果左邊窗格中列出一部以上的電腦，請選取應用程式程式碼所在的電腦。  
  
4. IIS 版本是在右窗格的 [ **版本** ] 欄中。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯程式 Web 應用程式的必要條件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)   
 [準備調試 ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)
