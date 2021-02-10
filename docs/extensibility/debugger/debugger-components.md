---
title: 偵錯工具元件 |Microsoft Docs
description: 瞭解組成 Visual Studio 偵錯工具所管理之偵錯工具的元素，這些專案會實作為 VSPackage。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de941be8c5535a2cef5995e3be9954ee32dcdc71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952443"
---
# <a name="debugger-components"></a>偵錯工具元件
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯工具會實作為 VSPackage 並管理整個偵錯工具會話。 Debug 會話包含下列元素：

- **Debug 封裝：**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無論正在進行什麼偵錯工具，偵錯工具都會提供相同的使用者介面。

- **會話 debug manager (SDM) ：** 提供與偵錯工具一致的程式設計介面，以 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理各種不同的偵錯工具引擎。 它是由所執行 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- **進程 debug manager (PDM) ：** 管理所有執行中的實例的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，這是可以進行或正在進行調試的所有程式清單。 它是由所執行 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

- **Debug engine (DE) ：** 負責監視正在進行程式設計的程式、將執行中程式的狀態傳達給 SDM 和 PDM，以及與運算式評估工具和符號提供者互動，以提供程式記憶體和變數狀態的即時分析。 它是由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (針對其支援的語言) ，以及想要支援其執行時間的協力廠商廠商所執行。

- **運算式評估工具 (EE) ：** 當程式在特定時間點停止時，提供動態評估使用者所提供之變數和運算式的支援。 它是由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 其支援的語言 (所執行，) 以及想要支援其專屬語言的協力廠商廠商。

- **(SP) 的符號提供者：** 也稱為符號處理常式，會將程式的偵錯工具符號對應至程式的執行中實例，以提供有意義的資訊 (例如原始程式碼層級的偵錯工具和運算式評估) 。 它是由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Common Language Runtime [CLR] 符號的 (和程式資料庫 [PDB] 符號檔格式所執行，) ，以及由有專屬方法可儲存偵錯工具的協力廠商廠商所執行。

  下圖顯示 Visual Studio 偵錯工具的這些元素之間的關聯性。

  ![調試元件總覽](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>本節內容
 [Debug 封裝](../../extensibility/debugger/debug-package.md) 討論在 shell 中執行， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 並處理所有 UI 的 debug 封裝。

 [進程偵錯工具管理員](../../extensibility/debugger/process-debug-manager.md) 提供 PDM 功能的總覽，也就是可以進行調試的進程管理員。

 [會話偵錯工具管理員](../../extensibility/debugger/session-debug-manager.md) 定義 SDM，以提供對 IDE 的偵錯工具的統一觀點。 SDM 管理 DE。

 [Debug 引擎](../../extensibility/debugger/debug-engine.md) 記錄 DE 提供的偵錯工具服務。

 [操作模式](../../extensibility/debugger/operational-modes.md) 概要說明 IDE 可以操作的三種模式：設計模式、執行模式和中斷模式。 也會討論轉換機制。

 [運算式評估](../../extensibility/debugger/expression-evaluator.md) 工具說明在執行時間的 EE 用途。

 [符號提供者](../../extensibility/debugger/symbol-provider.md) 討論在執行時，符號提供者如何評估變數和運算式。

 [型別視覺化器和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 討論何謂型別視覺化程式和自訂檢視器，以及運算式評估工具在支援這兩者時所扮演的角色。

## <a name="related-sections"></a>相關章節
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md) 描述主要的調試架構概念。

 [偵錯工具](../../extensibility/debugger/debugger-contexts.md) 內容說明如何在程式碼、檔和運算式評估內容中同時操作 DE。 描述每個內容的相關位置、位置或評估。

 [調試作業](../../extensibility/debugger/debugging-tasks.md) 包含各種偵錯工具的連結，例如啟動程式和評估運算式。

## <a name="see-also"></a>另請參閱
- [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
