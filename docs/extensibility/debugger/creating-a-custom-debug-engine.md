---
title: 建立自訂偵錯引擎 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67a58ab1bf508ba1b2edc7117412638de6c2231a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099542"
---
# <a name="create-a-custom-debug-engine"></a>建立自訂的偵錯引擎
偵錯引擎 (DE) 是元件，可讓特定的執行階段架構的偵錯。 通常是只有一個 DE 實作每個執行階段環境。

> [!NOTE]
>  TRANSACT-SQL 和 JScript 的個別 DE 實作時，VBScript 和 JScript 會共用單一的規定。

 規定適用於解譯器或作業的系統，以提供執行控制、 中斷點、 和運算式評估為這類偵錯服務。 這些服務透過 DE 介面實作，而且可能會造成偵錯工具不同的作業模式之間轉換。 如需詳細資訊，請參閱 <<c0> [ 作業模式](../../extensibility/debugger/operational-modes.md)。

 建立 DE 包含下列步驟：

1. 使用 Visual Studio 註冊 DE

2. 啟用要偵錯程式

3. 實作執行控制和狀態評估

4. 傳送事件

5. 設定終止並中斷連結

## <a name="in-this-section"></a>本節內容
 [註冊自訂的偵錯引擎](../../extensibility/debugger/registering-a-custom-debug-engine.md)說明使用 Visual Studio 中偵錯引擎註冊，讓它可以用所需的步驟。

 [啟用要偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)說明您 DE 可以偵錯程式之前，您必須先啟動 DE 或將它附加至現有的程式。

 [實作執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)偵錯應用程式為什麼需要實作執行控制功能的討論。

 [將事件傳送](../../extensibility/debugger/sending-events.md)之間偵錯工具，以 DE 說明通訊的事件模型根據 DCOM。

 [設定終止並中斷連結](../../extensibility/debugger/termination-and-detaching.md)說明如何達成正常終止時，這表示，沒有任何中斷點、 例外狀況、 執行階段錯誤或要進行偵錯應用程式中的無限迴圈。

 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)文件的偵錯工作階段中發生的事件呼叫的順序。

 [如何：偵錯自訂的偵錯引擎](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)說明如何偵錯自訂的規定。

## <a name="see-also"></a>另請參閱
- [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)