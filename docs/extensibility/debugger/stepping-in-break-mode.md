---
title: 在中斷模式中逐步執行 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb7b7e847c116f3aab38a12ec9801988bb8b3fc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111541"
---
# <a name="stepping-in-break-mode"></a>在中斷模式中逐步執行
下一節會說明當偵錯工具處於中斷模式，且必須逐步執行程式碼，就會發生的程序：

## <a name="stepping-process"></a>逐步執行程序

1. 呼叫[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)具有[STEPKIND](../../extensibility/debugger/reference/stepkind.md)並[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)執行之步驟的引數。

2. 完成步驟後，傳送[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)為停止事件。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)