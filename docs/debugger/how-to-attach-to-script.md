---
title: 如何： 附加至指令碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6769c4061487dc4b9279ff6ef9dffd36c2614775
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-attach-to-script"></a>如何：附加至指令碼
這個主題說明如何以手動方式將 Visual Studio 偵錯工具附加至指令碼檔以便進行偵錯。  
  
### <a name="to-attach-to-a-running-process"></a>若要附加至執行中的處理序  
  
1.  在 [ **偵錯** ] 功能表上，選擇 [ **附加至處理序**] (如果沒有任何專案開啟時，請選擇**附加至處理序**上**工具**功能表。)  
  
2.  在**附加至處理序**對話方塊中，查看**可用的處理序**清單，並且尋找指令碼處理您想要附加至。 您可以藉由查看找出指令碼處理序**類型**資料行。  
  
    1.  如果您要偵錯的處理序正執行於另一台電腦上，您必須先選取該遠端電腦。 如需詳細資訊，請參閱[如何： 選取遠端電腦](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba)。  
  
    2.  如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序]  核取方塊。  
  
    3.  如果您透過連接**遠端桌面連線**，選取**顯示所有工作階段中的處理序**核取方塊。  
  
3.  按一下您要附加的處理序。  
  
4.  在**附加至**方塊中，您應該會看到**指令碼**或**自動： 指令碼**。 如果看到其他項目，請遵照以下步驟：  
  
    1.  按一下 [選取] 。  
  
    2.  在**選取程式碼類型**對話方塊中，按一下 **偵錯這些程式碼類型**選取**指令碼**。  
  
    3.  按一下 [確定 **Deploying Office Solutions**]。  
  
5.  按一下 [附加] 。  
  
     此時，您可能會看到警告，指出 Internet Explorer 中已停用指令碼偵錯功能。 如果發生此情況，請參閱[警告： 指令碼偵錯已停用](../debugger/warning-script-debugging-disabled.md)。  
  
 [可使用的處理序]  清單會在您開啟 [處理序]  對話方塊時自動顯示。 當對話方塊開啟時，處理序可以在背景中啟動和停止。 所以，內容不一定是最新的。 您可以隨時按下查看目前的處理序清單重新整理清單**重新整理** 按鈕。  
  
 偵錯時，您可以附加至多個程式，但是無論在任何時間，偵錯工具一次只能有一個使用中程式。 您可在 [偵錯位置] 工具列中設定使用中程式。 如需詳細資訊，請參閱[How to： 設定目前的處理序](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)。  
  
 所有**偵錯**功能表執行命令都會影響使用中的程式。 您可以中斷偵錯的程式，從處理序 對話方塊。請參閱[使用中斷點](../debugger/using-breakpoints.md)。  
  
> [!NOTE]
>  如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱[安全性警告： 將附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)。  
  
 在某些情況下，在終端機服務 (遠端桌面) 工作階段中進行偵錯時，[可使用的處理序] 清單並不會顯示所有可使用的處理序。 在 [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] (含) 以後版本中，如果您是以受限制的使用者身分執行 Visual Studio，則 [可使用的處理序] 清單不會顯示在工作階段 0 中執行的處理序，因為工作階段 0 是用於服務以及其他包括 w3wp.exe 的伺服器處理序。 可藉由使用系統管理員帳戶來執行 Visual Studio，或是從伺服器主控台 (而非終端機服務工作階段) 執行 Visual Studio，來解決這個問題。 如果這些解決方法都不是可行的第三個選項是附加至處理序中，輸入 vsjitdebugger.exe-p ProcessId 在 Windows 命令列。 您可以使用 tlist.exe 來判斷處理序 ID。 若要取得 tlist.exe，下載並安裝 Debugging Tools for Windows，可在[Windows 硬體開發人員中心](http://go.microsoft.com/fwlink/?linkid=1651)。  
  
## <a name="see-also"></a>另請參閱  
 [用戶端指令碼偵錯](../debugger/client-side-script-debugging.md)   
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [安全性警告︰附加至未受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [偵錯工具安全性](../debugger/debugger-security.md)