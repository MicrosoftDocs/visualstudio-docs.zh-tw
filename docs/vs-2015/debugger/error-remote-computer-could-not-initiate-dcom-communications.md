---
title: 錯誤： 遠端電腦無法啟始 DCOM 通訊 |Microsoft Docs
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
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c86e5a193348a8f90e4888e0df3472d102beb08
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800870"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>錯誤：遠端電腦無法啟始 DCOM 通訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當遠端電腦嘗試與本機電腦進行通訊時，就會發生 DCOM 錯誤。 本機電腦是  
  
 執行 Visual Studio 的電腦。 發生這個錯誤的原因有下列幾種︰  
  
-   本機電腦啟用了防火牆。  
  
-   從遠端電腦到本機電腦的 Windows 驗證尚未運作。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  如果本機電腦已啟用的 Windows 防火牆，請參閱[設定 Up the Remote Tools 在裝置上](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)如需有關如何設定防火牆以供進行本機偵錯的指示。  
  
2.  測試 Windows 驗證，方法是嘗試從遠端伺服器上開啟本機電腦上的共用檔案。  
  
3.  若要還原 Windows 驗證，請嘗試重新啟動本機電腦和遠端電腦。 在本機和遠端機器上檢查 Kerberos 錯誤的事件日誌，並連絡網域系統管理員以瞭解已知的問題。  
  
## <a name="see-also"></a>另請參閱  
 [在裝置上設定遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



