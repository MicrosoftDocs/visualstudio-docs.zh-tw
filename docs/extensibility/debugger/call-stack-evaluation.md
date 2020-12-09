---
title: 呼叫堆疊評估 |Microsoft Docs
description: 瞭解 EnumFrameInfo 方法，以及如何在中斷模式期間，執行它以查看呼叫堆疊的堆疊框架。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fc637ff3ce2fe596eed48684523da7114fe0a03a
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914669"
---
# <a name="call-stack-evaluation"></a>呼叫堆疊評估
為了在中斷模式期間查看呼叫堆疊的堆疊框架，您必須執行 [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 方法。

## <a name="methods-for-evaluation"></a>評估的方法
 針對簡單的 debug 引擎 (DE) ，可能只有一個堆疊框架。 若要在中斷模式期間檢查堆疊框架，您必須執行下列 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|取得堆疊框架的程式碼內容。 程式碼內容代表堆疊框架中的目前指令指標。|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|取得堆疊框架的檔內容。 檔內容代表堆疊框架原始程式碼中的目前位置。 當您在程式中停止時，需要用來查看原始程式碼。|

 這些方法需要執行數個內容相關的介面和方法。 因此，您必須執行 [GetDocumentCoNtext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 方法和下列 [IDebugDocumentCoNtext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得檔內容的檔案語句範圍。|

 若要列舉程式碼內容，您必須執行 [IEnumDebugCodeCoNtexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)的所有方法。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
