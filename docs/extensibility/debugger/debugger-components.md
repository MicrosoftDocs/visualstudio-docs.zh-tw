---
title: 除錯器元件 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739005"
---
# <a name="debugger-components"></a>除錯器元件
除錯[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]器作為 VSPackage 實現,並管理整個調試會話。 除錯工作階段包括以下元素:

- **除錯包:**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯器提供相同的使用者介面,無論正在調試什麼。

- **工作階段除錯管理員 (SDM):** 為調試器提供一致的程式設計[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]介面,用於管理各種調試引擎。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實現。

- **程序除錯管理員 (PDM):** 管理 所有正在運行的實[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]例 ,可以調試或正在調試的所有程式的清單。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實現。

- **除錯引擎 (DE):** 負責監視正在調試的程式,將正在運行的程式的狀態傳達給 SDM 和 PDM,並與表達式賦值器和符號提供程式進行交互,以便對程式記憶體和變數的狀態提供即時分析。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](對於它支援的語言)和第三方供應商實現,他們希望支援自己的運行時。

- **運算式賦值器 (EE):** 支援在程式在特定點停止時動態計算使用者提供的變數和運算式。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](對於它支援的語言)和第三方供應商(希望支援自己的語言)實現。

- **符號提供者 (SP):** 也稱為符號處理程式,將程式的調試符號映射到程式的運行實例,以便提供有意義的資訊(如原始碼級調試和表達式計算)。 它由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](對於通用語言運行時 [CLR] 符號和程式資料庫 [PDB] 符號檔格式)和具有自己專有存儲調試資訊方法的第三方供應商實現。

  下圖顯示了可視化工作室調試器的這些元素之間的關係。

  ![除錯元件概述](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>本節內容
 [除錯套件](../../extensibility/debugger/debug-package.md)討論調試包,該包在shell[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中運行並處理所有UI。

 [程序除錯管理員](../../extensibility/debugger/process-debug-manager.md)提供 PDM 功能的概述,PDM 是可調試的進程的經理。

 [工作階段除錯管理員](../../extensibility/debugger/session-debug-manager.md)定義 SDM,它向 IDE 提供調試會話的統一視圖。 SDM 管理 DE。

 [偵錯引擎](../../extensibility/debugger/debug-engine.md)記錄 DE 提供的調試服務。

 [操作模式](../../extensibility/debugger/operational-modes.md)概述了 IDE 可以操作的三種模式:設計模式、運行模式和中斷模式。 還討論了過渡機制。

 [運算式賦值器](../../extensibility/debugger/expression-evaluator.md)解釋 EE 在運行時的用途。

 [符號提供者](../../extensibility/debugger/symbol-provider.md)討論符號提供程式在實現時如何計算變數和運算式。

 [類型視覺化器和自訂檢視器](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)討論什麼是類型可視化器和自定義查看器,以及表達式評估器在支援兩者方面扮演什麼角色。

## <a name="related-sections"></a>相關章節
 [除錯器概念](../../extensibility/debugger/debugger-concepts.md)描述主要的調試體系結構概念。

 [除錯器上下文](../../extensibility/debugger/debugger-contexts.md)說明 DE 如何在代碼、文檔和運算內容中同時運行。 描述三個上下文中的每一個與它相關的位置、位置或評估。

 [除錯工作](../../extensibility/debugger/debugging-tasks.md)包含指向各種除錯任務的連結,例如啟動程式和評估運算式。

## <a name="see-also"></a>另請參閱
- [開始使用](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
