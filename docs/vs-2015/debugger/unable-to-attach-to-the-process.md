---
title: 無法附加至處理程序 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e8f3e5b87879d34ab61f0b50e5e4b91e84933b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063084"
---
# <a name="unable-to-attach-to-the-process"></a>無法附加到處理序
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

無法附加至處理序。 當連接至這部電腦時，伺服器上的偵錯工具元件會收到拒絕存取。  
  
 有兩種常見的案例是造成此錯誤的原因：  
  
 **情節 1：** 電腦 A 正在執行 Windows XP。 電腦 B 執行的是 Windows Server 2003。 電腦 B 上的登錄會包含下列 DWORD 值：  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 使用者 1 在電腦 B 上啟動終端伺服器工作階段 (工作階段 1)，並從該工作階段啟動 Managed 應用程式。  
  
 使用者 2，兩台電腦上的系統管理員身分登入電腦 a。從該處，他或她嘗試附加至機器 b 上執行工作階段 1 中的應用程式  
  
 **案例 2:** 一個使用者登入了兩部機器，A 和 B，在相同群組中，兩台電腦上使用相同的密碼。 電腦 A 上執行偵錯工具，並嘗試附加至在電腦 b 上執行的受管理應用程式含有**網路存取：共用和安全性模式用於本機帳戶**設定為**客體**。  
  
### <a name="to-solve-scenario-1"></a>解決案例 1  
  
- 以相同使用者帳戶名稱和密碼，執行偵錯工具和 Managed 應用程式。  
  
### <a name="to-solve-scenario-2"></a>解決案例 2  
  
1. 在 [開始] 功能表內選擇 [控制台]。  
  
2. 在 [控制台] 中按兩下 [系統管理工具]。  
  
3. 在 [系統管理工具] 視窗中按兩下 [本機安全性原則]。  
  
4. 在 [本機安全性原則] 視窗中選取 [本機原則]。  
  
5. 在 **原則**資料行中，按兩下**網路存取：共用和安全性模式用於本機帳戶**。  
  
6. 在 **網路存取：共用和安全性模式用於本機帳戶**對話方塊方塊中，將本機安全性設定變更為**傳統**，然後按一下**確定**。  
  
    > [!CAUTION]
    >  將安全性模式變更為 [一般]，會導致未預期存取共用檔案和 DCOM 元件。 如果您做了此變更，遠端使用者可以使用您的本機使用者帳戶驗證，而非使用來賓帳戶。 如果遠端使用者符合您的使用者名稱和密碼，該使用者將可以存取您已共用的任何資料夾或 DCOM 物件。如果使用這個資訊安全模型，請確定電腦上的所有使用者帳戶皆有增強式密碼，或對偵錯中和已偵錯的電腦設定隔離的網路區段，以防止未經授權的存取。  
  
7. 關閉所有視窗。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
