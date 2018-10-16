---
title: 錯誤： 無法啟始 DCOM 通訊 |Microsoft Docs
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
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83b9bee3e67876ea941e3640c9f77906d8f53d96
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49277273"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>錯誤：無法啟始 DCOM 通訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當本機電腦 (Local Machine) 嘗試與遠端機器進行通訊時，就會發生 DCOM 錯誤。 這個錯誤發生的原因，是因為遠端伺服器上的防火牆，或是遠端機器上的 Windows 驗證中斷所造成。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果遠端電腦已啟用的 Windows 防火牆，請參閱[設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)如需有關如何設定防火牆以供進行本機偵錯的指示。  
  
-   若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。  
  
## <a name="see-also"></a>另請參閱  
 [Remote Debugging](../debugger/remote-debugging.md)



