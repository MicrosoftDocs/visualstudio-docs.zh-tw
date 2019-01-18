---
title: 偵錯資料繫結的 ActiveX 控制項 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6eae5820e7203b69ed6d08e398aef661d842906a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "53837845"
---
# <a name="debugging-a-data-bound-activex-control"></a>偵錯資料繫結的 ActiveX 控制項
如果您正在開發一個將繫結至資料來源控制項的 ActiveX 控制項，您可建立自己的容器應用程式，並使用該容器來偵錯 ActiveX 控制項。  
  
 例如，您可建立一個對話方塊架構的 MFC 應用程式，並將您的資料繫結控制項和資料來源控制項放在該對話方塊上。 您可將此 MFC 應用程式用於執行階段測試以及做為容器可執行檔，以便偵錯您的資料繫結 ActiveX 控制項。  
  
## <a name="using-the-test-container"></a>使用測試容器  
 如果您希望有一個可輕鬆修改的容器，以便在控制項或容器上支援不同的介面，請使用 ActiveX 測試容器 (Test Container) 做為偵錯工作階段的可執行檔。 在 ActiveX 測試容器中，按一下 [容器] 功能表內的 [選項]，以啟用不同的介面。 如需詳細資訊，請參閱 <<c0> [ 以測試容器測試屬性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)。  
  
 如果您在偵錯時，需要逐步執行容器的程式碼，請使用容器的偵錯版本，或使用 ActiveX 測試容器的偵錯版本。 如需詳細資訊，請參閱[TSTCON 範例：ActiveX 控制項測試容器。  
  
## <a name="see-also"></a>請參閱  
 [對 COM 和 ActiveX 進行偵錯](../debugger/com-and-activex-debugging.md)   
 [ActiveX 控制項](/cpp/mfc/activex-controls)