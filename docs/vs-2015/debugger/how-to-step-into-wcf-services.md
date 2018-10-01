---
title: 如何： 逐步執行 WCF 服務 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b779c8bc2e6da3975f1f70265482c706c9141375
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490754"
---
# <a name="how-to-step-into-wcf-services"></a>如何：逐步執行 WCF 服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 逐步執行 WCF 服務](https://docs.microsoft.com/visualstudio/debugger/how-to-step-into-wcf-services)。  
  
在 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 中，您可以逐步執行 WCF 服務。 如果 WCF 服務與用戶端都位於相同的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案，您就可以執行到達 WCF 服務內部的中斷點。  
  
 您必須在 app.config 或 Web.config 檔案內啟用偵錯，才能使用逐步執行。 如需如何啟用偵錯並逐步執行 WCF 服務的限制，請參閱 < [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
### <a name="to-step-into-a-wcf-service"></a>若要逐步執行 WCF 服務  
  
1.  建立 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案，其中包含 WCF 用戶端和 WCF 服務專案。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下 WCF 用戶端專案然後**設定為啟始專案**。  
  
3.  在 app.config 或 web.config 檔案內啟用偵錯。 如需詳細資訊，請參閱 < [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)。  
  
4.  在用戶端專案中要開始逐步執行的位置設定中斷點。 這通常會是在 WCF 服務呼叫之前。  
  
5.  執行至中斷點，然後開始逐步執行。 偵錯工具將自動逐步執行服務。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 WCF 服務](../debugger/debugging-wcf-services.md)   
 [WCF 偵錯的限制](../debugger/limitations-on-wcf-debugging.md)   
 [如何：偵錯自我裝載的 WCF 服務](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



