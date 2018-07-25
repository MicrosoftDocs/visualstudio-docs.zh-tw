---
title: 執行控制和狀態評估 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8961d2e06c7013b5667191c190053047f82de77d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232399"
---
# <a name="execution-control-and-state-evaluation"></a>執行控制和狀態評估
偵錯應用程式需要實作逐步執行函式、 中斷點、 停止和繼續執行這類執行控制項功能。 Visual Studio 偵錯基底偵錯工具元件之間傳送的事件其執行控制項。  
  
## <a name="in-this-section"></a>本節內容  
 [程式控制權](../../extensibility/debugger/program-control.md)  
 列出的程式層級發生下列常式： 設定下一個陳述式、 執行、 逐步執行、 繼續、 暫停及繼續。  
  
 [中斷點相關的方法](../../extensibility/debugger/breakpoint-related-methods.md)  
 定義繫結和暫止中斷點的 Visual Studio 支援的類型。  
  
 [呼叫堆疊評估](../../extensibility/debugger/call-stack-evaluation.md)  
 討論的方法，以便檢視呼叫堆疊的堆疊框架處於中斷模式時的實作。  
  
 [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 說明如何偵錯引擎 (DE) 中，運算式評估 (EE)，與工作階段偵錯管理員都能參與剖析並評估運算式輸入到其中一個 IDE 視窗。  
  
 [控制項事件](../../extensibility/debugger/control-events.md)  
 討論用來在受控制的程式執行期間傳送事件的介面。