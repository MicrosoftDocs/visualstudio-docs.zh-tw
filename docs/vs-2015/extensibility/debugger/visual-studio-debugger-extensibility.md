---
title: Visual Studio 偵錯工具擴充性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983660"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 偵錯工具的擴充性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 包含完全互動式的原始程式碼偵錯工具，提供強大且便於使用的工具，以追蹤程式中的 bug。 偵錯工具具有 Visual Basic、 C#、C/C++和 JavaScript 的完整支援。 不過，透過[Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=21835)提供的 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]，其他程式設計語言也可以在偵錯工具中支援，而且具有相同的豐富功能。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 偵錯工具是常見的前端（也就是使用者介面），而後者則是針對所要進行調試的語言。 針對新語言，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 偵錯工具支援所需的一切都是建立必要的後端元件，例如 debug engine （DE）。 這就是 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 的進入位置。  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 包含建立新的 DE 所需之所有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 元素的完整參考。 此外，還有一些範例和教學課程可協助您開始著手。  
  
 如需具有偵錯工具支援之語言專案系統的端對端範例，請參閱[IronPython 範例](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089)。  
  
 下列各節說明如何使用 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]擴充偵錯工具。  
  
## <a name="in-this-section"></a>本章節內容  
 [使用者入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 說明 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的調試功能，以及如何安裝 SDK。  
  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 記載自訂的刪除程式，從準備您的計畫，到解除卸離的過程。  
  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 說明您是否必須撰寫運算式評估工具。  
  
 [選擇偵錯引擎的實作策略](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 討論如何執行您的 DE。  
  
 [參考資料](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 記錄 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的調試 API。  
  
 [範例](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 包含 common language runtime 運算式評估工具範例和 debug engine 範例的連結。
