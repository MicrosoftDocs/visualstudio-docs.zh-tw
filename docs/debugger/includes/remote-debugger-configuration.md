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
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67043458"
---
1. 在遠端電腦中，尋找並啟動**遠端偵錯工具**從**開始**功能表。 
   
   如果您在遠端電腦上沒有系統管理權限，以滑鼠右鍵按一下**遠端偵錯工具**應用程式並選取**系統管理員身分執行**。 否則，只是它以正常方式啟動。

   如果您打算將附加至處理序執行身為管理員，或執行在不同的使用者帳戶 （例如 IIS)、 以滑鼠右鍵按一下**遠端偵錯工具**應用程式並選取**以系統管理員身分**. 如需詳細資訊，請參閱 <<c0> [ 系統管理員身分執行遠端偵錯工具](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator)。
   
1. 第一次啟動遠端偵錯工具 （或之前，您已設定它），**遠端偵錯組態** 對話方塊隨即出現。  
  
    ![遠端偵錯工具組態](../media/remotedebuggerconfwizardpage.png "遠端偵錯工具組態")  
  
1. 如果 Windows Web 服務 API 未安裝，只在 Windows Server 2008 R2 上發生這種情況，請選取**安裝** 按鈕。  
  
1. 選取您想要使用上的遠端工具的至少一個網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果電腦經由工作群組或家用群組連線，選擇適當的第二個或第三個項目。  
  
1. 選取 **設定遠端偵錯**設定防火牆並啟動遠端偵錯工具。  
  
1. 組態完成時，**遠端偵錯工具** 視窗隨即出現。
  
    ![遠端偵錯工具視窗](../media/remotedebuggerwindow.png "遠端偵錯工具視窗")
  
    遠端偵錯工具目前正在等待連接。 使用伺服器名稱和連接埠號碼顯示在 Visual Studio 中設定遠端連線設定。  
  
若要停止遠端偵錯工具，請選取**檔案** > **結束**。 您可以重新啟動從**啟動** 功能表中，或從命令列：  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
