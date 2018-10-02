---
title: 如何： 使用 RPC 偵錯對 COM 用戶端和伺服器 |Microsoft Docs
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
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b64c01f502dbe4194561776f121e21475d61d43
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487867"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>如何：使用 RPC 偵錯對 COM 用戶端和伺服器進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 偵錯 COM 用戶端和伺服器使用 RPC 偵錯](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-com-clients-and-servers-using-rpc-debugging)。  
  
您可使用遠端程序呼叫 (Remote Procedure Call，RPC) 偵錯功能，對 COM 用戶端/伺服器應用程式偵錯。 您必須啟用 RPC 偵錯才能使用它。 啟用 RPC 偵錯後，當您從用戶端逐步執行伺服器呼叫時，偵錯工具會附加至伺服器，讓您偵錯其程式碼。 附加偵錯工具後，您就能夠對用戶端和伺服器處理序，使用偵錯工具的所有功能。  
  
### <a name="to-enable-rpc-debugging"></a>若要啟用 RPC 偵錯  
  
1.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
2.  在 [**選項**] 對話方塊中，按一下**偵錯**資料夾。  
  
3.  按一下 **原生**頁面。  
  
4.  選取  **RPC 偵錯**核取方塊。  
  
    > [!NOTE]
    >  若要偵錯 RPC 呼叫，您必須擁有系統管理員 (Administrator) 或進階使用者 (Power User) 權限。  
  
    > [!NOTE]
    >  RPC 若逐步執行到執行 Microsoft Windows Vista 的遠端伺服器中，則只有在該遠端伺服器已附加原生偵錯工具的情況下才能運作。 否則，RPC 呼叫將會失敗，而且不會產生錯誤訊息。 要不然，RPC 呼叫將會完成，但逐步執行 RPC 呼叫將沒有作用。  
  
## <a name="see-also"></a>另請參閱  
 [COM 伺服器和容器偵錯](../debugger/com-server-and-container-debugging.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)



