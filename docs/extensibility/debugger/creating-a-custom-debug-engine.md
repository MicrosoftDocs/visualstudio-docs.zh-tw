---
title: 建立自定義除錯引擎 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739034"
---
# <a name="create-a-custom-debug-engine"></a>建立自訂除錯引擎
除錯引擎 (DE) 是允許除錯特定執行時體系結構的元件。 每個運行時環境通常只有一個 DE 實現。

> [!NOTE]
> 雖然 Transact-SQL 和 JScript 有單獨的 DE 實現,但 VBScript 和 JScript 共用單個 DE。

 DE 與解釋器或操作系統配合使用,提供執行控制、斷點和運算式計算等調試服務。 這些服務通過 DE 介面實現,並可能導致調試器在不同的操作模式之間轉換。 有關詳細資訊,請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。

 建立 DE 包括以下步驟:

1. 在視覺工作室註冊 DE

2. 開啟對程式進行除錯

3. 控制控制及狀態評估

4. 傳送事件

5. 設定終止與分離

## <a name="in-this-section"></a>本節內容
 [註冊自訂除錯引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)說明向 Visual Studio 註冊調試引擎以便可以使用它所需的步驟。

 [開啟對程式進行除錯](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)說明在 DE 可以除錯程式之前,必須先啟動 DE 或將其附加到現有程式。

 [控制控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)討論調試應用程式為什麼需要實現執行控制功能。

 [傳送事件](../../extensibility/debugger/sending-events.md)將除錯器和 DE 之間的通訊描述為基於 DCOM 的事件模型。

 [設定終止與分離](../../extensibility/debugger/termination-and-detaching.md)說明如何實現正常終止,這意味著要調試的應用程式中沒有斷點、異常、運行時錯誤或無限迴圈。

 [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)記錄調試會話中發生的事件的調用順序。

 [如何:除錯自訂除錯引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)說明如何調試自定義 DE。

## <a name="see-also"></a>另請參閱
- [視覺化工作室除錯器可擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
