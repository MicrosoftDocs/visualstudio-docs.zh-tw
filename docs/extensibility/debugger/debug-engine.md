---
title: "偵錯引擎 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70e572b73f8474f77a17989c790f2e7336f9d7a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="debug-engine"></a>偵錯引擎
偵錯引擎 (DE) 搭配運作的解譯器或作業系統提供偵錯服務，例如執行控制項、 中斷點及運算式評估。 DE 負責監視程式，偵錯時的狀態。 若要執行完成此動作，DE 會使用任何方法有它中支援的執行階段，是否將 cpu，或從應用程式開發介面由執行階段所提供。  
  
 例如，common language runtime (CLR) 提供機制來監視正在執行的程式，透過 ICorDebugXXX 介面。 支援 CLR DE 使用適當的 ICorDebugXXX 介面來追蹤偵錯 managed 程式碼程式。 它接著傳送至工作階段的偵錯管理員 (SDM)，這類將資訊轉送至其狀態的任何變更[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
> [!NOTE]
>  偵錯引擎為目標的特定執行階段，也就是系統中的程式進行偵錯執行。 CLR 的 managed 程式碼，執行階段，而 Win32 執行階段原生 Windows 應用程式。 如果您建立的語言可鎖定目標的這些兩個執行階段，其中一個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]已經提供必要的偵錯引擎。 您只需要實作是運算式評估工具。  
  
## <a name="debug-engine-operation"></a>偵錯引擎作業  
 監視服務會透過 DE 介面實作，而且可能會導致偵錯封裝，以便在不同的作業模式之間轉換。 如需詳細資訊，請參閱[作業模式](../../extensibility/debugger/operational-modes.md)。 通常是只有一個 DE 實作每個執行階段環境。  
  
> [!NOTE]
>  雖然有個別的 DE 實作方式，為 TRANSACT-SQL 和[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]，VBScript 和[!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]共用單一 DE。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯啟用偵錯引擎來執行下列其中一種： 在相同的程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層，或在目標程式相同的程序進行偵錯。 正在進行偵錯程序，實際執行的指令碼解譯器，而且偵錯引擎必須有深入的解譯器，才能監視指令碼時，通常會發生後者的表單。 請注意，在此情況下，解譯器是實際執行階段。偵錯引擎會針對特定執行階段實作。 此外，實作單一 DE 可以分割跨處理序與電腦界限 （例如，遠端偵錯）。  
  
 DE 公開[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯介面。 所有通訊都是透過 COM 是否 DE 載入同處理序、 處理不足，或在另一部電腦上，不會影響元件通訊。  
  
 DE 搭配以啟用該特定執行階段 DE，若要了解運算式的語法的運算式評估工具元件。 DE 也可以搭配符號處理常式元件存取的語言編譯器所產生的符號偵錯資訊。 如需詳細資訊，請參閱[運算式評估工具](../../extensibility/debugger/expression-evaluator.md)和[符號提供者](../../extensibility/debugger/symbol-provider.md)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [符號提供者](../../extensibility/debugger/symbol-provider.md)