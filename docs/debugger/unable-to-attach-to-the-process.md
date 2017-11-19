---
title: "無法附加至處理程序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec2c181edc69ac2e693de96fcf72fe9116f758b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="unable-to-attach-to-the-process"></a>無法附加到處理序
無法附加至處理序。 當連接至這部電腦時，伺服器上的偵錯工具元件會收到拒絕存取。  
  
 有兩種常見的案例是造成此錯誤的原因：  
  
 **案例 1:**電腦 A 正在執行 Windows XP。 電腦 B 執行的是 Windows Server 2003。 電腦 B 上的登錄會包含下列 DWORD 值：  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 使用者 1 在電腦 B 上啟動終端伺服器工作階段 (工作階段 1)，並從該工作階段啟動 Managed 應用程式。  
  
 使用者 2，兩台電腦上的系統管理員身份登入電腦 a從該處，他或她嘗試附加至電腦 b 上執行工作階段 1 中的應用程式  
  
 **案例 2:**一位使用者登入兩部電腦，A 和 B，在相同群組中，兩台電腦上使用相同的密碼。 電腦 A 上執行偵錯工具，而且嘗試附加至電腦 b 上執行的受管理應用程式已**網路存取： 共用和安全性模式用於本機帳戶**設**客體**。  
  
### <a name="to-solve-scenario-1"></a>解決案例 1  
  
-   以相同使用者帳戶名稱和密碼，執行偵錯工具和 Managed 應用程式。  
  
### <a name="to-solve-scenario-2"></a>若要解決案例 2  
  
1.  從**啟動**功能表上，選擇**控制台**。  
  
2.  在控制台中，按兩下**系統管理工具**。  
  
3.  在 [系統管理工具] 視窗中，按兩下**本機安全性原則**。  
  
4.  在 [本機安全性原則] 視窗中，選取**本機原則**。  
  
5.  在**原則**資料行中，按兩下**網路存取： 共用和安全性模式用於本機帳戶**。  
  
6.  在**網路存取： 共用和安全性模式用於本機帳戶**對話方塊方塊中，變更本機安全性設定，以便**傳統**，按一下**確定**。  
  
    > [!CAUTION]
    >  將安全性模式變更為 [一般]，會導致未預期存取共用檔案和 DCOM 元件。 如果您做了此變更，遠端使用者可以使用您的本機使用者帳戶驗證，而非使用來賓帳戶。 如果遠端使用者符合您的使用者名稱和密碼，該使用者將可以存取您已共用的任何資料夾或 DCOM 物件。如果使用這個安全性模式，請確定電腦上的所有使用者帳戶皆有增強式密碼，或對偵錯中和已偵錯的電腦設定隔離的網路區段，以防止未經授權的存取。  
  
7.  關閉所有視窗。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)