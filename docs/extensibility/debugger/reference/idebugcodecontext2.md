---
title: IDebugCodeContext2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734220"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
此介面表示代碼指令的起始位置。 對於當今的大多數運行時體系結構,可以將代碼上下文視為程序執行流中的位址。

## <a name="syntax"></a>語法

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>實施者說明
 調試引擎實現此介面,將代碼指令的位置與文檔位置相關聯。

## <a name="notes-for-callers"></a>通話備註
 許多介面上的方法傳回此介面,最常見的是[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。 它還廣泛用於[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)介面以及斷點解析度資訊。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|獲取與活動代碼上下文對應的文檔上下文。|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|獲取此代碼上下文的語言資訊。|

## <a name="remarks"></a>備註
 介面和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面之間的主要區別是,始終`IDebugCodeContext2`與指令對齊。 `IDebugCodeContext2` 這意味著`IDebugCodeContext2`始終指向指令的開頭,而`IDebugMemoryContext2`可以指向運行時體系結構中的任何位元組記憶體。 `IDebugCodeContext2`由指令而不是基本儲存大小(通常位元組)遞增。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
