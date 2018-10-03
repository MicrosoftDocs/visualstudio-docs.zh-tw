---
title: 偵錯工具元件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b1b8f12a8bfa15a352f38d021a64a6f9f8b9244
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488396"
---
# <a name="debugger-components"></a>偵錯工具元件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[偵錯工具元件](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-components)。  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯工具會實作為 VSPackage 和管理整個偵錯工作階段。 偵錯工作階段包含下列項目：  
  
-   **偵錯封裝：** [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯工具會提供相同的使用者介面，不論項目正在進行偵錯。  
  
-   **工作階段偵錯管理員 (SDM):** 提供一致的程式設計介面，以[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯工具進行偵錯引擎的各種不同的管理。 它由實作[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
-   **處理序偵錯管理員 (PDM):** 的所有執行的執行個體的管理， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，可以是或正在進行偵錯的所有程式的清單。 它由實作[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
-   **偵錯引擎 (DE):** 須負責監視正在偵錯程式進行通訊的 SDM 和 PDM，執行中的程式狀態，並與其互動的運算式評估工具和符號提供者，以提供即時的分析程式的記憶體和變數的狀態。 它由實作[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]（適用於支援的語言） 和第三方廠商想要支援他們自己的執行的階段。  
  
-   **運算式評估工具 (EE):** 提供支援以動態方式評估變數和使用者所提供的程式已停止在特定時間點時的運算式。 它由實作[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]（適用於支援的語言） 和第三方廠商想要支援他們自己的語言。  
  
-   **符號提供者 (SP):** 也稱為符號處理常式，將對應程式的偵錯的符號至程式的執行個體以便可提供有意義的資訊 （例如來源-程式碼層級偵錯和運算式評估）。 它由實作[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]（Common Language runtime [CLR] 符號與程式資料庫 [PDB] 符號檔案格式） 和具有自己專屬的方法，儲存偵錯資訊的第三方廠商所提供。  
  
 下圖顯示 Visual Studio 偵錯工具的這些項目之間的關聯性。  
  
 ![偵錯元件概觀](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>本節內容  
 [偵錯封裝](../../extensibility/debugger/debug-package.md)  
 討論偵錯封裝，在執行[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]殼層，會處理所有的使用者介面。  
  
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
 [快速入門](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

