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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50915123"
---
1. 在遠端電腦中，尋找並啟動**遠端偵錯工具**從**開始**功能表。 
   
   如果您在遠端電腦上沒有系統管理權限，以滑鼠右鍵按一下**遠端偵錯工具**應用程式並選取**系統管理員身分執行**。 否則，只是它以正常方式啟動。

   可能有不同版本的*msvsmon.exe*中*x64*， *x32*，或其他資料夾。 請確定在開始您需要偵錯您的應用程式的版本。 
   
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
