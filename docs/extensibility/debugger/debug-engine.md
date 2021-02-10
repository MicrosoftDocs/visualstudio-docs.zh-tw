---
title: Debug Engine |Microsoft Docs
description: 瞭解 debug engine 如何與解譯器或作業系統搭配使用，以提供執行控制、中斷點和運算式評估等服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e278b83e69a063c88b4cb3ff48d919d2b07ea6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955160"
---
# <a name="debug-engine"></a>Debug 引擎
Debug engine (DE) 可搭配解譯器或作業系統使用，以提供偵錯工具，例如執行控制、中斷點和運算式評估。 DE 負責監視正在進行偵錯工具的狀態。 為了達成此目的，在支援的執行時間中，不論是從 CPU 或執行時間所提供的 Api，DE 都會使用任何可用的方法。

 例如，common language runtime (CLR) 提供可透過 ICorDebugXXX 介面監視執行中程式的機制。 支援 CLR 的 DE 會使用適當的 ICorDebugXXX 介面來追蹤要進行調試的 managed 程式碼程式。 然後，它會將任何狀態變更傳達給會話 debug manager (SDM) ，以將這類資訊轉送至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。

> [!NOTE]
> 偵錯工具引擎以特定的執行時間為目標，也就是要在其中執行正在進行程式設計的程式的系統。 CLR 是 managed 程式碼的執行時間，而 Win32 執行時間則適用于原生 Windows 應用程式。 如果您建立的語言可以設定為這兩個執行時間的其中一個，則 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 已提供必要的偵錯工具引擎。 您只需要執行運算式評估工具。

## <a name="debug-engine-operation"></a>Debug engine 作業
 監視服務是透過 DE 介面來執行，而且可能會使 debug 封裝在不同的操作模式之間轉換。 如需詳細資訊，請參閱 [操作模式](../../extensibility/debugger/operational-modes.md)。 在每個執行時間環境中，通常只會執行一次 DE。

> [!NOTE]
> 雖然 Transact-sql 和 VBScript 都有不同的取消執行 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] ，並且會 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] 共用單一 de。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 偵錯工具可讓 debug engine 以兩種方式執行：在和 shell 相同的進程中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，或與正在進行調試的目的程式相同的進程中。 第二個表單通常發生于正在進行調試的進程實際上是在解譯器下執行的腳本時。 Debug engine 必須熟悉解譯器，才能監視腳本。 在此情況下，解譯器實際上是執行時間;偵錯工具引擎適用于特定的執行時間。 此外，單一 DE 的執行可以跨進程和電腦界限進行分割 (例如，遠端偵錯程式) 。

 DE 會公開 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 調試的介面。 所有通訊都是透過 COM 進行。 無論是在進程內、跨進程或在另一部電腦上載入 DE，都不會影響元件通訊。

 DE 可搭配運算式評估工具元件使用，以啟用該特定執行時間的 DE 來瞭解運算式的語法。 也可以使用符號處理常式元件來存取語言編譯器所產生的符號偵錯工具資訊。 如需詳細資訊，請參閱 [運算式評估](../../extensibility/debugger/expression-evaluator.md) 工具和 [符號提供者](../../extensibility/debugger/symbol-provider.md)。

## <a name="see-also"></a>另請參閱
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
- [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)
- [符號提供者](../../extensibility/debugger/symbol-provider.md)
