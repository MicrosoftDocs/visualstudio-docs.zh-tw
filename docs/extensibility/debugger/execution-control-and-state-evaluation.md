---
title: "執行控制項和狀態的評估 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5ebc9d78f50454a0b0576c4d339102b08cb3e26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="execution-control-and-state-evaluation"></a>執行控制項和狀態評估
偵錯應用程式需要實作逐步執行函式、 中斷點、 停止和繼續執行這類執行控制項功能。 Visual Studio 偵錯基底偵錯工具元件之間傳送的事件其執行控制項。  
  
## <a name="in-this-section"></a>本節內容  
 [程式控制](../../extensibility/debugger/program-control.md)  
 列出的程式層級發生下列常式： 設定下一個陳述式、 執行、 逐步執行、 繼續、 暫停及繼續。  
  
 [中斷點相關的方法](../../extensibility/debugger/breakpoint-related-methods.md)  
 定義繫結和暫止中斷點的 Visual Studio 支援的類型。  
  
 [呼叫堆疊評估](../../extensibility/debugger/call-stack-evaluation.md)  
 討論可讓在中斷模式期間的呼叫堆疊的堆疊框架檢視方法的實作。  
  
 [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 說明如何偵錯引擎 (DE) 中，運算式評估 (EE)，與工作階段偵錯管理員都能參與剖析，並評估運算式輸入到其中一個 IDE 視窗。  
  
 [控制項事件](../../extensibility/debugger/control-events.md)  
 討論用來控制執行程式期間傳送事件的介面。