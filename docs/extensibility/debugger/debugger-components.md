---
title: 偵錯工具元件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea47a75ef943b462b35c06b20b9cd21b2ade7b70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894255"
---
# <a name="debugger-components"></a>偵錯工具元件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會實作為 VSPackage 和管理整個偵錯工作階段。 偵錯工作階段包含下列項目：  
  
- **偵錯封裝：**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會提供相同的使用者介面，不論項目正在進行偵錯。  
  
- **工作階段偵錯管理員 (SDM):** 提供一致的程式設計介面，以[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具進行偵錯引擎的各種不同的管理。 它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
- **處理序偵錯管理員 (PDM):** 管理的所有執行的執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以是或正在進行偵錯的所有程式的清單。 它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
- **偵錯引擎 (DE):** 負責監視程式，偵錯，通訊 SDM 和 PDM，執行程式的狀態，並與其互動的運算式評估工具和符號提供者提供的程式的記憶體狀態的即時分析和變數。 它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（適用於支援的語言） 和第三方廠商想要支援他們自己的執行的階段。 
  
- **運算式評估工具 (EE):** 提供支援以動態方式評估變數和使用者所提供的程式已停止在特定時間點時的運算式。 它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（適用於支援的語言） 和第三方廠商想要支援他們自己的語言。  
  
- **符號提供者 (SP):** 也稱為符號處理常式，將對應程式的偵錯的符號至程式的執行個體以便可提供有意義的資訊 （例如來源-程式碼層級偵錯和運算式評估）。 它由實作[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（Common Language runtime [CLR] 符號與程式資料庫 [PDB] 符號檔案格式） 和具有自己專屬的方法，儲存偵錯資訊的第三方廠商所提供。  
  
  下圖顯示 Visual Studio 偵錯工具的這些項目之間的關聯性。  
  
  ![偵錯元件概觀](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>本節內容  
 [偵錯封裝](../../extensibility/debugger/debug-package.md)  
 討論偵錯封裝，在執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，會處理所有的使用者介面。  
  
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)  
 提供 PDM，也就是可偵錯的處理程序管理員的功能概觀。  
  
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)  
 定義在 SDM 提供 ide 的偵錯工作階段的統一的檢視。 在 SDM 管理裝置。  
  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)  
 文件 DE 提供偵錯服務。  
  
 [作業模式](../../extensibility/debugger/operational-modes.md)  
 提供三種模式能 IDE 的概觀： 設計模式、 執行的模式中和中斷模式。 此外，也會討論轉換機制。  
  
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)  
 在執行階段說明 EE 的目的。  
  
 [符號提供者](../../extensibility/debugger/symbol-provider.md)  
 討論如何進行，請在實作中，符號提供者會評估變數和運算式。  
  
 [類型視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 討論何謂類型視覺化檢視和自訂檢視器是和中同時支援扮演的角色，運算式評估工具。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明 DE 的運作方式同時在程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估與它相關的每個軸。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)