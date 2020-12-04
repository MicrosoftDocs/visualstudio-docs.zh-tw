---
title: 執行控制和狀態評估 |Microsoft Docs
description: 瞭解 Visual Studio 的偵錯工具如何以偵錯工具元件之間所傳送之事件的執行控制為基礎。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 021fab07cfaf1ec17821a8ef9a33a03f2d6ec714
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560898"
---
# <a name="execution-control-and-state-evaluation"></a>執行控制和狀態評估
若要對應用程式進行偵錯工具，您必須將這類執行控制功能實作為逐步執行函式、在中斷點停止，然後繼續執行。 Visual Studio 的偵錯工具會根據偵錯工具元件之間傳送的事件來執行控制項的執行控制。

## <a name="in-this-section"></a>本節內容
 [程式控制](../../extensibility/debugger/program-control.md) 列出程式層級所發生的下列常式：設定下一個語句、執行、逐步執行、繼續、暫停和繼續。

 [中斷點相關的方法](../../extensibility/debugger/breakpoint-related-methods.md) 定義 Visual Studio 支援之中斷點的系結和暫止型別。

 [呼叫堆疊評估](../../extensibility/debugger/call-stack-evaluation.md) 討論在中斷模式期間，允許查看呼叫堆疊堆疊框架的方法的執行方式。

 [運算式評估](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) 說明 debug engine (DE) 、運算式評估 (EE) ，以及會話 debug manager 如何剖析和評估輸入至 IDE 其中一個視窗的運算式。

 [控制事件](../../extensibility/debugger/control-events.md) 討論在受控制的程式執行期間用來傳送事件的介面。
