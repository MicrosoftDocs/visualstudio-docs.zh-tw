---
title: HOW TO：逐步執行 WCF 服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ad5ca2d74a1c141b9687d9b9eac5d8b3e268cc0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939334"
---
# <a name="how-to-step-into-wcf-services"></a>HOW TO：逐步執行 WCF 服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，您可以逐步執行 WCF 服務。 如果 WCF 服務與用戶端都位於相同的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案，您就可以執行到達 WCF 服務內部的中斷點。  
  
 您必須在 app.config 或 Web.config 檔案內啟用偵錯，才能使用逐步執行。 如需如何啟用偵錯並逐步執行 WCF 服務的限制，請參閱 < [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### <a name="to-step-into-a-wcf-service"></a>若要逐步執行 WCF 服務  
  
1.  建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案，其中包含 WCF 用戶端和 WCF 服務專案。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下 WCF 用戶端專案，然後按一下 [設定為啟始專案]。  
  
3.  在 app.config 或 web.config 檔案內啟用偵錯。 如需詳細資訊，請參閱 < [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
4.  在用戶端專案中要開始逐步執行的位置設定中斷點。 這通常會是在 WCF 服務呼叫之前。  
  
5.  執行至中斷點，然後開始逐步執行。 偵錯工具將自動逐步執行服務。  
  
## <a name="see-also"></a>另請參閱  
 [對 WCF 服務進行偵錯](../debugger/debugging-wcf-services.md)   
 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：針對自我裝載的 WCF 服務進行偵錯](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
