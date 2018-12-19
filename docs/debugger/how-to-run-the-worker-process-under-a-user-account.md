---
title: 執行背景工作處理序的使用者帳戶 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47aefcb73fd20dcc82b19ed6200fec5fd57dd486
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067812"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>HOW TO：在使用者帳戶下執行背景工作處理序
若要設定電腦以便在某個使用者帳戶下執行 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序 (aspnet_wp.exe 或 w3wp.exe)，請依照下列步驟執行。  

 > [!IMPORTANT]
 > 從 Windows Server 2008 R2 開始，我們建議您使用[ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities)做為每個應用程式集區識別。
  
## <a name="procedure"></a>程序  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>若要在使用者帳戶下執行 aspnet_wp.exe  
  
1. 開啟 machine.config 檔，這個檔案位於電腦中安裝執行階段之路徑下的 CONFIG 資料夾內。  
  
2. 尋找 &lt;processModel&gt; 區段，然後將 user 和 password 屬性變更為您要用來執行 aspnet_wp.exe 之使用者帳戶的名稱和密碼。  
  
3. 儲存 machine.config 檔。  
  
4. 在 [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)]中，預設是安裝 IIS 6.0。 對應的背景工作處理序是 w3wp.exe。若要以 aspnet_wp.exe 做為背景工作處理序在 IIS 6.0 模式中執行，您必須執行下列步驟：  
  
   1.  依序按一下 [ **開始**]、[ **系統管理工具** ]，然後選擇 [ **網際網路資訊服務**]。  
  
   2.  在 [ **網際網路資訊服務** ] 對話方塊中，以滑鼠右鍵按一下 [ **網站** ] 資料夾，然後選擇 [ **屬性**]。  
  
   3.  在 [ **網站屬性** ] 對話方塊中，選擇 [ **服務**]。  
  
   4.  選取 [ **以 IIS 6.0 隔離模式執行 WWW 服務**]。  
  
   5.  關閉 [ **屬性** ] 對話方塊以及 [ **網際網路服務管理員**]。  
  
5. 開啟 Windows 命令提示，然後執行下列命令重設伺服器：  
  
   ```cmd
   iisreset  
   ```  
   — 或 —  
  
   ```cmd
   net stop iisadmin /y  
   net start w3svc  
   ```  
  
6. 找出 Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files 資料夾，它應該與 CONFIG 資料夾位於相同的路徑中。 以滑鼠右鍵按一下 [Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files] 資料夾，然後選擇捷徑功能表上的 [屬性]  。  
  
7. 在 [ **暫存 ASP.NET 檔案屬性** ] 對話方塊內，按一下 [ **安全性** ] 索引標籤。  
  
8. 按一下 [ **進階**]。  
  
9. 在 [ **暫存 ASP.NET 檔案的進階安全性設定** ] 對話方塊中，按一下 [ **加入**]。  
  
    [ **選取使用者、電腦或群組** ] 對話方塊隨即出現。  
  
10. 在 [ **請輸入物件名稱來選取** ] 方塊中輸入使用者名稱，然後按一下 [ **確定**]。 使用者名稱必須遵循以下格式：DomainName\UserName。  
  
11. 在 [ **暫存 ASP.NET 檔的使用權限項目** ] 對話方塊中，授與使用者 [ **完全控制**]，然後按一下 [ **確定** ] 來關閉 [ **暫存 ASP.NET 檔案的項目** ] 對話方塊。  
  
12. [ **安全性** ] 對話方塊隨即出現，詢問您是否真的想要變更系統資料夾的使用權限。 按一下 [ **是**]。  
  
13. 按一下 [ **確定** ] 以關閉此 [ **暫存 ASP.NET 檔案屬性** ] 對話方塊。  
  
## <a name="see-also"></a>請參閱  
[針對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[ASP.NET 偵錯：系統需求](../debugger/aspnet-debugging-system-requirements.md)  
  
