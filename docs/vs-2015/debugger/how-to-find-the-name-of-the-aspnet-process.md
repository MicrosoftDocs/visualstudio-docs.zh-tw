---
title: 如何： 尋找 ASP.NET 處理序的名稱 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6b036fdd9f75afc0c9976591ae0df23194b196d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268901"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>如何：尋找 ASP.NET 處理序的名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要附加至執行中的 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式，您必須知道 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 處理序的名稱：  
  
-   如果您執行的是 IIS 6.0 或 IIS 7.0，則名稱是 w3wp.exe。  
  
-   如果您執行的是 IIS 的先前版本，則名稱是 aspnet_wp.exe。  
  
 使用所建置之應用程式[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]或更新版本中，[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]程式碼可以位於檔案系統，並在 WebDev.WebServer.exe 測試伺服器下執行。 在此情況下，您需要附加至 WebDev.WebServer.exe，而非 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 處理序。 本案例僅適用於本機偵錯。  
  
 舊版 ASP 應用程式會在它們以同處理序 (In-Process) 方式執行時，於 IIS 處理序 inetinfo.exe 中執行。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>若要判斷專案程式碼是位於檔案系統或 IIS 上  
  
1.  在 Visual Studio 中開啟**方案總管 中**如果它尚未開啟。  
  
2.  選取包含應用程式名稱的最上層節點。  
  
3.  如果**屬性**位於檔案系統上的應用程式程式碼時，視窗標題中包含檔案路徑。  
  
     否則，請**屬性**視窗標題將包含網站的名稱。  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>若要判斷應用程式在哪一個 IIS 版本下執行  
  
1.  尋找**系統管理工具**並加以執行。 根據您的作業系統，這可能是中的圖示**控制台中**，或當您按一下時出現的功能表項目**開始**。  
  
     在 Windows XP**控制台中**可以在 類別檢視 」 或 「 傳統檢視。 您必須在類別目錄檢視中，按一下**切換到傳統檢視**或是**效能及維護**若要查看**系統管理工具**圖示。  
  
2.  從**系統管理工具**，執行 Internet Information Services。 MMC 對話方塊就會出現。  
  
3.  如果左邊窗格中列出一部以上的電腦，請選取應用程式程式碼所在的電腦。  
  
4.  IIS 版本是位於**版本**右窗格的資料行。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯 Web 應用程式的必要條件](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [系統需求](../debugger/aspnet-debugging-system-requirements.md)   
 [準備偵錯 ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [偵錯 Web 應用程式和指令碼](../debugger/debugging-web-applications-and-script.md)



