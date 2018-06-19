---
title: Visual Studio 偵錯工具擴充性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5bb01c093fda068dfbc7dfa705914a8bdef4d2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127066"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 偵錯工具擴充性
Visual Studio 包含完整的互動式來源的程式碼偵錯工具，提供功能強大且容易使用的工具來追蹤程式中的 bug。 偵錯工具有完整的支援 Visual Basic、 C#、 C/c + + 和 JavaScript。 不過，在使用[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，也就是可從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453)，其他程式設計語言的支援相同的豐富功能的偵錯工具。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具是常見的前端 （也就是使用者介面），因此，偵錯的語言專屬的偵錯元件。 對新語言，所有所需的支援由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會建立必要的後端元件，例如偵錯引擎 (DE)。 這是 where[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]傳入。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]包含所有的完整參考[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建立新的 DE 所需的項目。 此外，還有範例和教學課程將協助您開始。  
  
 如需偵錯支援的語言專案系統的端對端範例，請參閱[IronPython 範例](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089)。  
  
 下列各節說明如何使用偵錯工具來擴充[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 說明該怎麼辦[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯提供項目，以及如何安裝 SDK。  
  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 文件的自訂 DE 程序，來卸離 DE DE 準備您的程式。  
  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 說明您的電腦必須撰寫的運算式評估工具。  
  
 [選擇偵錯引擎的實作策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 討論如何實作您 DE。  
  
 [參考資料](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 文件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯應用程式開發介面。  
  
 [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 包含通用語言執行階段運算式評估工具範例和偵錯引擎範例連結。
