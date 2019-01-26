---
title: Visual Studio 偵錯工具擴充性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04031c2307d5d91a4854678f810f87b5afde0627
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952154"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 偵錯工具擴充性
Visual Studio 包含具全面互動性的來源的程式碼偵錯工具，提供功能強大且容易使用的工具來追蹤您的程式中的 bug。 偵錯工具會有完整支援 Visual Basic、 C#、 C/c + + 和 JavaScript。 不過，透過[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]，也就是可從[Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453)，其他程式設計語言可支援在相同的豐富功能的偵錯工具中。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具，在開啟，正在進行偵錯的語言專屬的偵錯元件是常見的前端 （也就是使用者介面）。 新的語言，取得所需的所有支援的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具是建立必要的後端元件，例如偵錯引擎 (DE)。 此時正是[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]傳入。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]包含所有的完整參考[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]建立新的裝置所需的項目。 此外，還有範例和可幫助您入門的教學課程。  
  
 偵錯支援的語言專案系統的完整範例，請參閱 < [IronPython 範例](https://www.microsoft.com/download/details.aspx?id=55984)。  
  
 下列各節說明如何使用偵錯工具來擴充[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
 [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 說明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯的供應項目，以及如何安裝 SDK。  
  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 文件的自訂 DE 程序，來卸離 DE DE 正在準備您的程式。  
  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 說明您的電腦必須撰寫的運算式評估工具。  
  
 [選擇 偵錯引擎的實作策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 討論如何實作您的裝置。  
  
 [參考資料](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 文件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯 API。  
  
 [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 包含連結的通用語言執行階段運算式評估工具範例和偵錯引擎範例。
