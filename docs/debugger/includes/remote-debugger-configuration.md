---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149207"
---
1. 在遠端電腦上，從 [**開始**] 功能表尋找並啟動**遠端偵錯程式**。 
   
   如果您在遠端電腦上沒有系統管理許可權，請以滑鼠右鍵按一下 [**遠端偵錯**程式] 應用程式，然後選取 [**以系統管理員身分執行**]。 否則，只要正常啟動它。

   如果您打算附加至以系統管理員身分執行，或在不同的使用者帳戶（例如 IIS）下執行的進程，請在**遠端偵錯**程式應用程式上按一下滑鼠右鍵，然後選取 [以**系統管理員身分執行**]。 如需詳細資訊，請參閱[以系統管理員身分執行遠端偵錯程式](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator)。
   
1. 當您第一次啟動遠端偵錯程式（或設定之前）時，會出現 [**遠端**偵測設定] 對話方塊。  
  
    ![遠端偵錯程式]設定(../media/remotedebuggerconfwizardpage.png "遠端偵錯程式")設定  
  
1. 如果未安裝 Windows Web 服務 API，這只會發生在 Windows Server 2008 R2 上，請選取 [**安裝**] 按鈕。  
  
1. 選取至少一個您想要使用遠端工具的網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果電腦是透過工作組或家庭系統進行連線，請視需要選擇第二個或第三個專案。  
  
1. 選取 [**設定遠端偵錯**程式] 以設定防火牆並啟動遠端偵錯程式。  
  
1. 設定完成時，[**遠端偵錯程式**] 視窗隨即出現。
  
    ![遠端偵錯程式視窗](../media/remotedebuggerwindow.png "遠端偵錯程式視窗")
  
    遠端偵錯程式現在正在等候連接。 使用顯示的伺服器名稱和埠號碼，在 Visual Studio 中設定遠端連線設定。  
  
若要停止遠端偵錯程式，**請選取 [** 檔案] [結束]  >  ** **。 您可以從 [**開始**] 功能表或從命令列重新開機它：  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
