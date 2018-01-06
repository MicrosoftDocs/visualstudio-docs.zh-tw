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
ms.openlocfilehash: cfb41cf6274238fef2de9b74496a33fba110e04f
ms.sourcegitcommit: fb73b56d45ebc0386cd4de1a706ba9e20c59daf1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
您必須在遠端電腦上擁有管理權限。  
  
1.  尋找遠端偵錯工具應用程式。 (它已經安裝，在位置中找到 msvsmon.exe，或開啟 [開始] 功能表，並搜尋**遠端偵錯工具**。)
  
     如果您在遠端伺服器上執行遠端偵錯工具，您可以以滑鼠右鍵按一下 遠端偵錯工具應用程式，並選擇**系統管理員身分執行**。 如果您不遠端伺服器上執行它，只要正常方式啟動。
  
3.  當您啟動遠端工具第一次 （或在設定之前），則**遠端偵錯組態** 對話方塊隨即出現。  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Windows 服務應用程式開發介面未安裝 （這只在 Windows Server 2008 R2 上發生），如果選擇**安裝** 按鈕。  
  
5.  選取您想要在遠端工具上使用的網路類型。 必須至少選取一種網路類型。 如果此電腦經由網域連線，您就必須選擇第一個項目。 如果此電腦經由工作群組或家用群組連線，您就需要視情況選擇第二個或第三個項目。  
  
6.  選擇**設定遠端偵錯**設定防火牆並啟動工具。  
  
7.  設定完成時，[遠端偵錯工具] 視窗隨即出現。
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     遠端偵錯工具目前正在等待連接。 記下的伺服器名稱和通訊埠號碼會顯示，因為這必須符合您稍後使用 Visual Studio 中的組態。  
  
 當您完成偵錯，必須先停止遠端偵錯工具時，按一下 **檔案 > 結束**視窗上。 您可以重新啟動從**啟動**功能表或從命令列：  
  
 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具\\< x86、 x64 或 Appx > \msvsmon.exe**。  
