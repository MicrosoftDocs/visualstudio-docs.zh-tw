---
title: "錯誤： 無法啟始 DCOM 通訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c80f2455b53cba46f0f2f753c55ff1b7e9dad8d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>錯誤：無法啟始 DCOM 通訊
當本機電腦 (Local Machine) 嘗試與遠端機器進行通訊時，就會發生 DCOM 錯誤。 這個錯誤發生的原因，是因為遠端伺服器上的防火牆，或是遠端機器上的 Windows 驗證中斷所造成。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果遠端電腦已啟用 Windows 防火牆，請參閱[遠端偵錯](../debugger/remote-debugging.md)如需有關如何設定用於本機偵錯防火牆的指示。  
  
-   若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯](../debugger/remote-debugging.md)