---
title: 錯誤： 目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ae98de5ac5062bd55a3818b82e1f6ba771b612
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499615"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>錯誤：目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[錯誤： 目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦](https://docs.microsoft.com/visualstudio/debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer)。  
  
這個錯誤指出，Visual Studio 遠端偵錯工具服務正在某個使用者帳戶下執行，但是當該帳戶嘗試連接您在其中進行偵錯的電腦時無法進行驗證。  
  
 下表顯示可以存取該電腦的帳戶：  
  
|||||  
|-|-|-|-|  
||LocalSystem 帳戶|網域帳戶|在兩台電腦上都具有相同使用者名稱和密碼的本機帳戶|  
|兩台電腦都位於相同的網域|是|是|是|  
|網域上具有雙向信任的兩台電腦|否|否|是|  
|工作群組中的一或兩台電腦|否|否|是|  
|不同網域上的電腦|否|否|是|  
  
 此外：  
  
-   您用來執行 Visual Studio 遠端偵錯工具服務的帳戶，必須是遠端機器上的系統管理者，這樣才能偵錯任何處理序。  
  
-   這個帳戶也必須授與`Log on as a service`正在使用的遠端電腦上的權限**本機安全性原則**系統管理工具。  
  
-   如果您使用本機帳戶存取電腦，就必須在本機帳戶下執行 Visual Studio 遠端偵錯工具服務。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定已在遠端電腦上正確設定 Visual Studio 遠端偵錯工具服務。 如需詳細資訊，請參閱 <<c0> [ 設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)。  
  
2.  在可以存取偵錯工具主機電腦的帳戶下執行遠端偵錯工具服務，如上表所示。  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>若要加入「以服務方式登入」權限  
  
1.  在 **開始**功能表上，選擇**控制台**。  
  
2.  在 [控制台] 中選擇**傳統檢視**，如有必要。  
  
3.  連按兩下 [系統管理工具] 。  
  
4.  在 [系統管理工具] 視窗中，按兩下**本機安全性原則**。  
  
5.  在 [**本機安全性設定**] 視窗中，展開**本機原則**資料夾。  
  
6.  按一下 **使用者權限指派**。  
  
7.  中**原則**資料行中，按兩下**以服務方式登**若要檢視目前的本機群組原則指派，在**登入為服務** 對話方塊。  
  
8.  若要加入新的使用者，請按一下**新增使用者或群組** 按鈕。  
  
9. 當您完成新增使用者時，請按一下**確定**。  
  
### <a name="to-work-around-this-error"></a>若要解決這個錯誤  
  
-   將遠端偵錯監視當成應用程式執行，不要當成服務執行。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [遠端偵錯](../debugger/remote-debugging.md)



