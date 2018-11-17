---
title: 錯誤： 工作群組遠端登入失敗 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723659"
---
# <a name="error-workgroup-remote-logon-failure"></a>錯誤：工作群組遠端登入失敗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這個錯誤為：  
  
 登入失敗：不明的使用者名稱或錯誤密碼  
  
 **原因**  
  
 當您從工作群組上的電腦進行偵錯並嘗試連接遠端機器時，就可能會發生這個錯誤。 可能的原因包括：  
  
-   遠端機器上沒有符合名稱和密碼的帳戶。  
  
-   如果 Visual Studio 電腦和遠端電腦位於工作群組，因為預設值，會發生此錯誤**本機安全性原則**設定遠端電腦上。 預設值**本機安全性原則**設定為**僅適用於來賓-本機使用者以 Guest 驗證**。 偵錯在這個安裝上，您必須變更遠端電腦上的設定**一般-本機使用者自我驗證**。  
  
> [!NOTE]
>  您必須是系統管理員，才能進行下列工作。  
  
### <a name="to-open-the-local-security-policy-window"></a>若要開啟本機安全性原則視窗  
  
1.  開始**secpol.msc** Microsoft Management Console 嵌入式管理單元。 在 Windows [搜尋]、Windows [執行] 方塊或在 [命令提示字元] 中輸入 secpol.msc。  
  
### <a name="to-add-user-rights-assignments"></a>若要加入使用者權限指派  
  
1.  Open the Loca  
  
2.  開啟**本機安全性原則**視窗。  
  
3.  依序展開**本機原則**資料夾。  
  
4.  按一下 **使用者權限指派**。  
  
5.  在**原則**資料行中，按兩下**偵錯程式**若要檢視目前的本機群組原則指派，在**本機安全性原則設定** 對話方塊。  
  
     ![本機安全性原則的使用者權限](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  若要加入新的使用者，請按一下**新增使用者或群組** 按鈕。  
  
### <a name="to-change-the-sharing-and-security-model"></a>若要變更共用和安全性模式  
  
1.  開啟**本機安全性原則**視窗。  
  
2.  依序展開**本機原則**資料夾。  
  
3.  按一下 **安全性選項**。  
  
4.  在 **原則**資料行中，按兩下**網路存取： 共用和安全性模式用於本機帳戶**。  
  
5.  在 **網路存取： 共用和安全性模式用於本機帳戶**對話方塊方塊中，將值變更為**一般-本機使用者自我驗證**，按一下 **套用** 按鈕。  
  
     ![本機安全性原則安全性選項](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



