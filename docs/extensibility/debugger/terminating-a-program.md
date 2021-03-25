---
title: 終止程式 |Microsoft Docs
description: 本文說明 IDE 如何使用 debug engine，以單一線程終止單一程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: db67e0a391f40fc17a80e616e10aa46a600337a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057854"
---
# <a name="terminating-a-program"></a>終止程式
下一節說明使用一個執行緒的單一程式終止。

## <a name="termination-process"></a>終止進程

1. DE 會傳送具有有效[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)的[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) 。

2. DE 會傳送具有有效[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)的[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 。

   IDE 進入設計模式。 偵錯工具引擎或執行時間環境會呼叫 [IDebugPortNotify2：： RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) ，以從埠中移除程式。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
