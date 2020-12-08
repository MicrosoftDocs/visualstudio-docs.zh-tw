---
title: 在中斷模式中逐步執行 |Microsoft Docs
description: 深入瞭解偵錯工具處於中斷模式時所發生的進程。 偵錯工具必須接著逐步執行程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845189"
---
# <a name="stepping-in-break-mode"></a>在中斷模式中逐步執行
下一節將描述偵錯工具處於中斷模式，且必須逐步執行程式碼時所發生的進程：

## <a name="stepping-process"></a>逐步執行流程

1. 使用[STEPKIND](../../extensibility/debugger/reference/stepkind.md)和[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)引數呼叫[IDebugProgram2：： step](../../extensibility/debugger/reference/idebugprogram2-step.md)來執行步驟。

2. 當步驟完成時，傳送 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 做為停止事件。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
