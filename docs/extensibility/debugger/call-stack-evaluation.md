---
title: 呼叫堆疊評估 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739186"
---
# <a name="call-stack-evaluation"></a>呼叫堆疊評估
為了在中斷模式下查看調用堆疊的堆疊幀,必須實現[EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)方法。

## <a name="methods-for-evaluation"></a>評價方法
 對於簡單的調試引擎 (DE),可能只有一個堆疊幀。 要在中斷模式下檢查堆疊幀,必須實現[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)的以下方法。

|方法|描述|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|獲取堆疊幀的代碼上下文。 代碼上下文表示堆疊框架中的當前指令指標。|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|獲取堆疊框架的文檔上下文。 文檔上下文表示堆疊幀的原始程式碼中的當前位置。 在程式中停止時查看原始程式碼所需的。|

 這些方法需要實現多個與上下文相關的介面和方法。 因此,您必須實現[GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)方法和[IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)的以下方法。

|方法|描述|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|獲取文檔上下文的檔語句範圍。|

 要枚舉代碼上下文,必須實現[IEnumDebugCodeContext2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)的所有方法。

## <a name="see-also"></a>另請參閱
- [執行控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
