---
title: 執行控制和狀態評估 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738749"
---
# <a name="execution-control-and-state-evaluation"></a>執行控制及狀態評估
調試應用程式需要實現諸如步進函數、在斷點停止和繼續執行等執行控制功能。 Visual Studio 除錯以除錯器元件之間發送的事件,其執行控制。

## <a name="in-this-section"></a>本節內容
 [程式控制](../../extensibility/debugger/program-control.md)列出了在程式級別發生的以下例程:設置下一個語句、執行、步進、繼續、掛起和恢復。

 [與斷點相關的方法](../../extensibility/debugger/breakpoint-related-methods.md)定義 Visual Studio 支援的綁定和掛起的斷點類型。

 [呼叫堆疊評估](../../extensibility/debugger/call-stack-evaluation.md)討論允許在中斷模式下查看調用堆疊堆疊幀的方法的實現。

 [運算運算](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)說明除錯引擎 (DE)、表示式運算 (EE) 和工作階段除錯管理員如何參與對輸入到 IDE 視窗之一的表示式的解析和評估。

 [控制事件](../../extensibility/debugger/control-events.md)討論用於在程式受控執行期間發送事件的介面。
