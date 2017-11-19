---
title: "偵錯工具元件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec2b7a18dac9616db1743a50539c2860caca2e26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugger-components"></a>偵錯工具元件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會實作為 VSPackage 和管理整個偵錯工作階段。 偵錯工作階段包含下列項目：  
  
-   **偵錯封裝：** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會提供相同的使用者介面，無論正在偵錯功能。  
  
-   **工作階段偵錯管理員 (SDM):**提供一致的程式設計介面，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具的各種不同的偵錯引擎的管理。 它藉由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **處理序偵錯管理員 (PDM):**管理的所有執行的執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，可以是或正在進行偵錯的所有程式的清單。 它藉由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
-   **偵錯引擎 (DE):**會負責監視程式，偵錯時，通訊 SDM 和 PDM，執行程式的狀態，並與其互動來提供即時分析的運算式評估工具和符號提供者程式的記憶體和變數的狀態。 它藉由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（適用於支援語言版本） 和第三方廠商想要支援他們自己的執行的階段。  
  
-   **運算式評估工具 (EE):**提供支援動態評估變數和程式已停止的特定點時，使用者所提供的運算式。 它藉由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（適用於支援語言版本） 和第三方廠商想要支援他們自己的語言。  
  
-   **符號提供者 (SP):**也稱為符號處理常式對應程式的偵錯符號至程式的執行個體，以便可以提供有意義的資訊 （例如來源的程式碼層級偵錯和運算式評估）。 它藉由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（如 Common Language Runtime [CLR] 符號與程式資料庫 [PDB] 符號檔案格式） 和協力廠商儲存偵錯資訊的自己專屬的方法。  
  
 下圖顯示 Visual Studio 偵錯工具的這些項目之間的關聯性。  
  
 ![元件偵錯概觀](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>本章節內容  
 [偵錯封裝](../../extensibility/debugger/debug-package.md)  
 討論偵錯封裝，在中執行[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，會處理所有的使用者介面。  
  
 [處理序偵錯管理員](../../extensibility/debugger/process-debug-manager.md)  
 提供 PDM，也就是可進行偵錯的處理程序管理員的功能概觀。  
  
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)  
 定義 SDM，ide 提供偵錯工作階段的統一的檢視。 SDM 管理 DE。  
  
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)  
 文件 DE 提供偵錯服務。  
  
 [作業模式](../../extensibility/debugger/operational-modes.md)  
 提供概觀能 IDE 的三種模式： 設計模式中，執行的模式中和中斷模式。 也會討論轉換的機制。  
  
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)  
 在執行階段說明 EE 的目的。  
  
 [符號提供者](../../extensibility/debugger/symbol-provider.md)  
 討論如何在實作中，符號提供者會評估變數和運算式。  
  
 [類型視覺化檢視和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 討論什麼類型的視覺化檢視和自訂檢視器和角色同時支援扮演運算式評估工具。  
  
## <a name="related-sections"></a>相關章節  
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯工具內容](../../extensibility/debugger/debugger-contexts.md)  
 說明如何 DE 同時中運作的程式碼、 文件和運算式評估內容。 描述三個內容、 位置、 位置或評估適用於它的每個軸。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種不同的偵錯工作，例如啟動程式，以及評估運算式的連結。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)