---
title: 在中斷模式中逐步執行 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423357"
---
# <a name="stepping-in-break-mode"></a>在中斷模式中逐步執行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明偵錯工具處於中斷模式且必須逐步執行程式碼時所發生的進程：  
  
## <a name="stepping-process"></a>逐步執行流程  
  
1. 使用[STEPKIND](../../extensibility/debugger/reference/stepkind.md)和[STEPUNIT](../../extensibility/debugger/reference/stepunit.md)引數呼叫[IDebugProgram2：： step](../../extensibility/debugger/reference/idebugprogram2-step.md)來執行步驟。  
  
2. 當步驟完成時，傳送 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 做為停止事件。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
