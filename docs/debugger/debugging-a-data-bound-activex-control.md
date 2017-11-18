---
title: "偵錯資料繫結的 ActiveX 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c1ffd73919b4788e9c0151a636539faceea5300
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-a-data-bound-activex-control"></a>偵錯資料繫結的 ActiveX 控制項
如果您正在開發一個將繫結至資料來源控制項的 ActiveX 控制項，您可建立自己的容器應用程式，並使用該容器來偵錯 ActiveX 控制項。  
  
 例如，您可建立一個對話方塊架構的 MFC 應用程式，並將您的資料繫結控制項和資料來源控制項放在該對話方塊上。 您可將此 MFC 應用程式用於執行階段測試以及做為容器可執行檔，以便偵錯您的資料繫結 ActiveX 控制項。  
  
## <a name="using-the-test-container"></a>使用測試容器  
 如果您希望有一個可輕鬆修改的容器，以便在控制項或容器上支援不同的介面，請使用 ActiveX 測試容器 (Test Container) 做為偵錯工作階段的可執行檔。 在 ActiveX 測試容器中，按一下 **選項**從**容器**功能表來啟用不同的介面。 如需詳細資訊，請參閱[使用測試容器測試屬性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)。  
  
 如果您在偵錯時，需要逐步執行容器的程式碼，請使用容器的偵錯版本，或使用 ActiveX 測試容器的偵錯版本。 如需詳細資訊，請參閱[TSTCON 範例： ActiveX 控制項測試容器](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600)。  
  
## <a name="see-also"></a>另請參閱  
 [COM 和 ActiveX 的偵錯](../debugger/com-and-activex-debugging.md)   
 [ActiveX 控制項](/cpp/mfc/activex-controls)