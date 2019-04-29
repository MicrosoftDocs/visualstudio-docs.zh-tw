---
title: 呼叫堆疊評估 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b61a5455e965b4c89ffadd3c01a95bd1baf0a181
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926007"
---
# <a name="call-stack-evaluation"></a>呼叫堆疊評估
若要檢視呼叫堆疊的堆疊框架處於中斷模式時，您必須實作[EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。

## <a name="methods-for-evaluation"></a>評估方法
 針對簡單的偵錯引擎 (DE)，可能只有一個堆疊框架。 若要檢查的堆疊框架處於中斷模式時，您必須實作下列方法[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)。

|方法|描述|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|取得堆疊框架的程式碼內容。 程式碼內容代表目前指令指標框架中。|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得堆疊框架的文件內容。 文件內容代表堆疊框架的原始程式碼中的目前位置。 檢視原始碼，當您在程式中被停止時的必要項。|

 這些方法需要的數個內容相關的介面和方法的實作。 因此，您必須實作[GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)方法和下列方法[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)。

|方法|描述|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得文件內容的檔案陳述式範圍。|

 若要列舉的程式碼內容，您必須實作的所有方法[IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)