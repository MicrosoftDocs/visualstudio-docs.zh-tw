---
title: 偵錯引擎 |Microsoft Docs
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
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89f2c2fafb397246a8a2df8dab7d59a361edc11c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491735"
---
# <a name="debug-engine"></a>偵錯引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[偵錯引擎](https://docs.microsoft.com/visualstudio/extensibility/debugger/debug-engine)。  
  
偵錯引擎 (DE) 適用於解譯器或作業系統，來提供偵錯的服務，例如執行控制、 中斷點、 和運算式評估。 DE 負責監視正在偵錯程式的狀態。 若要執行達到此目的，DE 會使用任何方法會為它提供的支援的執行階段，是否執行階段所提供的 cpu，或從 Api。  
  
 例如，common language runtime (CLR) 會提供機制來監視正在執行的程式，透過 ICorDebugXXX 介面。 支援 CLR DE 會使用適當的 ICorDebugXXX 介面，來追蹤正在偵錯 managed 程式碼程式。 然後通訊狀態的任何變更工作階段的偵錯管理員 (SDM)，將這類資訊轉送給[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE。  
  
> [!NOTE]
>  偵錯引擎為目標的特定執行階段，也就是系統中的程式進行偵錯執行。 CLR 執行階段為了在 managed 程式碼，而 Win32 執行階段原生 Windows 應用程式。 如果您建立的語言可以為其中一個這些兩個執行階段，目標[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]已提供必要的偵錯引擎。 您必須實作的只是運算式評估工具。  
  
## <a name="debug-engine-operation"></a>偵錯引擎作業  
 監視服務會透過 DE 介面實作，而且會造成偵錯封裝至不同的作業模式之間轉換。 如需詳細資訊，請參閱 <<c0> [ 作業模式](../../extensibility/debugger/operational-modes.md)。 通常是只有一個 DE 實作每個執行階段環境。  
  
> [!NOTE]
>  雖然有不同的 DE 實作，為 TRANSACT-SQL 以及[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]，VBScript 和[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]共用單一 DE。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 偵錯啟用偵錯引擎來執行下列其中一種： 在相同的程序[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]殼層，或在相同的程序，做為目標的程式進行偵錯。 處理序偵錯是實際解譯器、 下執行的指令碼和偵錯引擎必須有深切的解譯器，才能監視指令碼時，通常會發生後者的表單。 請注意，在此情況下，解譯器是實際執行階段;偵錯引擎會針對特定執行階段實作。 此外，實作單一 DE 可以分割跨處理序與電腦界限 （例如，遠端偵錯）。  
  
 DE 公開[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]偵錯介面。 所有通訊都是透過 com。 是否同處理序、 處理外，或在另一部電腦上載入 DE 時，它不會影響元件通訊。  
  
 DE 搭配運算式評估工具元件，來啟用該特定執行階段 DE，若要了解運算式的語法。 DE 也適用於一個符號處理常式元件，可存取由語言編譯器所產生的符號偵錯資訊。 如需詳細資訊，請參閱 <<c0> [ 運算式評估工具](../../extensibility/debugger/expression-evaluator.md)並[符號提供者](../../extensibility/debugger/symbol-provider.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)   
 [運算式評估工具](../../extensibility/debugger/expression-evaluator.md)   
 [符號提供者](../../extensibility/debugger/symbol-provider.md)

