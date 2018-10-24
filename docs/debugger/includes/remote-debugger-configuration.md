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
ms.openlocfilehash: 252c505260986bd08b5522ba79d1e00a82624241
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942955"
---
您必須具有系統管理權限在遠端電腦上。  
  
1. 尋找遠端偵錯工具應用程式。 (在它已安裝的位置找到 msvsmon.exe 或開啟 [開始] 功能表和搜尋**遠端偵錯工具**。)
  
    如果您在遠端伺服器上執行遠端偵錯工具，您可以以滑鼠右鍵按一下 遠端偵錯工具應用程式，並選擇**系統管理員身分執行**。 如果您不會執行它，在遠端伺服器上，只是正常方式啟動。
  
2. 當您啟動遠端工具第一次 （或在設定之前），則**遠端偵錯組態** 對話方塊隨即出現。  
  
    ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. 如果 Windows 服務 API 未安裝 （這只能在 Windows Server 2008 R2 上發生），請選擇**安裝** 按鈕。  
  
4. 選取您想要在遠端工具上使用的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就需要視情況選擇第二個或第三個項目。  
  
5. 選擇**設定遠端偵錯**設定防火牆並啟動此工具。  
  
6. 設定完成時，[遠端偵錯工具] 視窗隨即出現。
  
    ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    遠端偵錯工具目前正在等待連接。 請記下的伺服器名稱和連接埠號碼會顯示，因為這必須符合您稍後使用 Visual Studio 中的組態。  
  
   當您完成偵錯 」 和 「 停止遠端偵錯工具的需要時，按一下**檔案 > 結束**視窗上。 您可以重新啟動從**啟動**功能表或從命令列：  
  
   **\<遠端偵錯工具安裝目錄 >\\< x86、 x64、 ARM、 ARM64 或 Appx > \msvsmon.exe**。  
