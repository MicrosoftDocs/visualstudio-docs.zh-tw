---
title: 除錯引擎 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739060"
---
# <a name="debug-engine"></a>偵錯引擎
除錯引擎 (DE) 與直譯器或作業系統配合使用,以提供除錯服務,如執行控制、斷點和運算運算。 DE 負責監視正在調試的程序的狀態。 為此,DE 使用受支援的運行時可用的任何方法,無論是從 CPU 還是從運行時提供的 API。

 例如,通用語言運行時 (CLR) 提供機制,透過 ICorDebugXXX 介面監視正在運行的程式。 支援 CLR 的 DE 使用適當的 ICorDebugXXX 介面來追蹤正在除錯的託管代碼程式。 然後,它將狀態的任何更改傳達給會話調試管理器 (SDM),該管理器將此類資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]轉發給 IDE。

> [!NOTE]
> 調試引擎以特定運行時為目標,即運行正在調試的程式的系統。 CLR 是託管代碼的運行時,Win32 運行時適用於本機 Windows 應用程式。 如果創建的語言可以針對這兩個運行時之一,則[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已提供必要的調試引擎。 所有要實現的只是表達式賦值器。

## <a name="debug-engine-operation"></a>除錯引擎操作
 監視服務透過 DE 介面實現,並可能導致調試包在不同的操作模式之間轉換。 有關詳細資訊,請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。 每個運行時環境通常只有一個 DE 實現。

> [!NOTE]
> 雖然對 Transact-SQL[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]和 (VBScript)[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]有單獨的 DE 實現,並且共用單個 DE。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]除錯使除錯引擎能夠執行以下兩種方式之一:要麼與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]shell 在同一進程中,要麼與正在調試的目標程式在同一進程中運行。 當正在調試的進程實際上是在解釋器下運行的腳本時,通常會出現後一種形式。 調試引擎必須對解釋器有深入的瞭解才能監視腳本。 在這種情況下,解釋器實際上是一個運行時;調試引擎適用於特定的運行時實現。 此外,單個 DE 的實現可以跨進程和電腦邊界(例如遠端調試)拆分。

 DE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]公開調試介面。 所有通信均通過 COM。 無論 DE 是在進程內、進程外加載還是在另一台電腦上載入,都不會影響元件通訊。

 DE 與表達式賦值器元件配合使用,使該特定運行時的 DE 能夠理解表達式的語法。 DE 還與符號處理程式元件一起訪問語言編譯器生成的符號調試資訊。 有關詳細資訊,請參閱[表示式賦值器](../../extensibility/debugger/expression-evaluator.md)和[符號提供者](../../extensibility/debugger/symbol-provider.md)。

## <a name="see-also"></a>另請參閱
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
- [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)
- [符號提供者](../../extensibility/debugger/symbol-provider.md)
