---
title: 建立自訂的 Debug Engine |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 241bc016d8a64905951bffef07ba425f1351a727
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903579"
---
# <a name="create-a-custom-debug-engine"></a>建立自訂的調試引擎
「偵錯工具引擎」（DE）是一種元件，可讓您進行特定執行時間架構的偵錯工具。 在每個執行時間環境中，通常只會有一個 DE 的執行。

> [!NOTE]
> 雖然 Transact-sql 和 JScript 有不同的 DE 執行，但是 VBScript 和 JScript 共用了一個 DE。

 DE 會使用解譯器或作業系統來提供這類的偵錯工具服務，做為執行控制、中斷點和運算式評估。 這些服務是透過 DE 介面來執行，而且可能會導致偵錯工具在不同的操作模式之間轉換。 如需詳細資訊，請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。

 建立 DE 包含下列步驟：

1. 向 Visual Studio 註冊 DE

2. 讓程式能夠進行調試

3. 執行控制和狀態評估

4. 傳送事件

5. 設定終止和卸離

## <a name="in-this-section"></a>本節內容
 [註冊自訂的 debug engine](../../extensibility/debugger/registering-a-custom-debug-engine.md)說明向 Visual Studio 註冊 debug engine 所需的步驟，以便可以使用它。

 [讓程式能夠進行調試](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)說明您必須先啟動或將它附加至現有的程式，才能讓您的程式進行 debug。

 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)討論為什麼應用程式需要執行控制功能。

 [傳送事件](../../extensibility/debugger/sending-events.md)描述偵錯工具和 DE 之間的通訊，這是以 DCOM 為基礎的事件模型。

 [設定終止和卸離](../../extensibility/debugger/termination-and-detaching.md)說明如何達到正常終止，這表示應用程式中不會有任何中斷點、例外狀況、執行時間錯誤或無限迴圈可供進行調試。

 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)記載在調試會話中發生之事件的呼叫順序。

 [如何： debug 自訂的 debug engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)說明如何將自訂的 DE 進行 debug。

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
