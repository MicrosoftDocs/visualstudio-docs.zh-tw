---
title: 建立自訂的 Debug Engine |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839177"
---
# <a name="creating-a-custom-debug-engine"></a>建立自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debug engine (DE) 是一種元件，可讓您進行特定執行時間架構的偵錯工具。 在每個執行時間環境中，通常只會執行一次 DE。  
  
> [!NOTE]
> 雖然 Transact-sql 和 JScript 之間有不同的 DE 實作為，但 VBScript 和 JScript 共用單一 DE。  
  
 DE 適用于解譯器或作業系統，以提供這類的偵錯工具，做為執行控制、中斷點和運算式評估。 這些服務是透過 DE 介面來執行，而且可能會導致偵錯工具在不同的操作模式之間轉換。 如需詳細資訊，請參閱 [操作模式](../../extensibility/debugger/operational-modes.md)。  
  
 建立 DE 是由下列步驟所組成：  
  
1. 向 Visual Studio 註冊 DE  
  
2. 啟用要進行調試的程式  
  
3. 執行控制和狀態評估  
  
4. 傳送事件  
  
5. 終止和卸離  
  
## <a name="in-this-section"></a>本節內容  
 [註冊自訂的偵錯引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 說明使用 Visual Studio 註冊 debug engine 的必要步驟，以便能夠使用它。  
  
 [啟用要偵錯的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 說明在您的 DE 可以錯程式之前，您必須先將它取消或附加至現有的程式。  
  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 討論為什麼應用程式必須執行執行控制功能的偵錯工具。  
  
 [傳送事件](../../extensibility/debugger/sending-events.md)  
 描述偵錯工具與 DE （以 DCOM 為基礎的事件模型）之間的通訊。  
  
 [終止並中斷連結](../../extensibility/debugger/termination-and-detaching.md)  
 說明如何達到正常終止，這表示在要進行調試的應用程式中沒有中斷點、例外狀況、執行階段錯誤或無限迴圈。  
  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)  
 記錄在偵錯工具會話中發生之事件的呼叫順序。  
  
 [如何：偵錯自訂的偵錯引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 說明如何進行自訂 DE 的調試。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯工具的擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
