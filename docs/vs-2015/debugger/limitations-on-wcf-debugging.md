---
title: WCF 偵錯的限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c1d569712547144067cbfcfd894e31e1b41964e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798308"
---
# <a name="limitations-on-wcf-debugging"></a>WCF 偵錯的限制
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用三種方式開始對 WCF 服務進行偵錯：  
  
- 您要對呼叫服務的用戶端處理序進行偵錯。 偵錯工具會逐步執行服務。 服務不需要與用戶端應用程式位於相同的方案內。  
  
- 您要對要求服務的用戶端處理序進行偵錯。 服務必須是方案的一部分。  
  
- 您使用**附加至處理序**附加至目前執行的服務。 偵錯會從服務內部開始進行。  
  
  本主題將描述這些情節的限制。  
  
## <a name="limitations-on-stepping-into-a-service"></a>逐步執行服務的限制  
 若要從您要進行偵錯的用戶端應用程式逐步執行服務，則必須符合下列條件：  
  
-   用戶端必須使用同步用戶端物件呼叫服務。  
  
-   協定作業不可以是單向的。  
  
-   如果伺服器非同步，您就無法在服務內部執行程式碼時檢視完整的呼叫堆疊。  
  
-   您必須在 app.config 或 Web.config 檔案中使用下列程式碼啟用偵錯：  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     這個程式碼只需要加入一次。 藉由編輯.config 檔案，或藉由使用附加至服務，您可以新增此程式碼**附加至處理序**。 當您使用**附加至處理序**服務偵錯程式碼會自動新增至.config 檔案。 完成這個動作後，您就可以進行偵錯及逐步執行服務，而不需要編輯 .config 檔案。  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>跳離服務的限制  
 跳離服務並返回用戶端的限制，與逐步執行服務所述的限制相同。 此外，您必須將偵錯工具附加至用戶端。 如果您要對用戶端進行偵錯並逐步執行服務，則偵錯工具會保持附加至服務的狀態。 這適用於使用來啟動用戶端是否**開始偵錯**或使用附加至用戶端**附加至處理序**。 如果您藉由附加至服務的方式開始進行偵錯，則偵錯工具尚未附加至用戶端。 在此情況下，如果您必須跳離服務並傳回給用戶端，您必須先使用**附加至處理序**以手動方式附加至用戶端。  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>自動附加至服務的限制  
 自動附加至服務具有下列限制：  
  
-   服務必須是您要偵錯之 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案的一部分。  
  
-   服務必須已裝載。 服務可以是網站專案 (檔案系統和 HTTP)、Web 應用程式專案 (檔案系統和 HTTP)，或 WCF 服務庫專案的一部分。 WCF 服務庫專案可以是服務庫或工作流程服務庫。  
  
-   服務必須從 WCF 用戶端叫用。  
  
-   您必須在 app.config 或 Web.config 檔案中使用下列程式碼啟用偵錯：  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>自我裝載  
 A*自我裝載的服務*是 iis 中，WCF 服務主機，不會執行的 WCF 服務或[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]程式開發伺服器。 如需如何偵錯自我裝載的服務的資訊，請參閱[如何： 偵錯自我裝載 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)。  
  
## <a name="self-hosting"></a>自我裝載  
 若要啟用的偵錯[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3.0 或 3.5 應用程式[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]之前，則必須安裝 3.0 或 3.5[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]安裝。 如果[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]之前先安裝[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3.0 或 3.5，就會發生錯誤時您嘗試偵錯[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]3.0 或 3.5 應用程式。 錯誤訊息為「無法自動逐步執行伺服器」。 若要修正此問題，請使用 Windows**控制台中**，**程式和功能**修復您[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]安裝。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)   
 [如何：偵錯自我裝載的 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



