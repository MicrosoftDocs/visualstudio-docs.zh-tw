---
description: 此介面代表程式碼指令的開始位置。
title: IDebugCodeCoNtext2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 228b6e84ca2f85803c4a248b966698b822bb572f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164093"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
此介面代表程式碼指令的開始位置。 在現今大部分的執行時間架構中，可以將程式碼內容視為程式執行資料流程中的位址。

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine 會執行這個介面，將程式碼指令的位置與檔位置產生關聯。

## <a name="notes-for-callers"></a>呼叫者注意事項
 許多介面上的方法會傳回這個介面，最常見的是 [GetCodeCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。 它也廣泛用於 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) 介面以及中斷點解析資訊。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了 [IDebugMemoryCoNtext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|取得對應至使用中程式碼內容的檔內容。|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|取得此程式碼內容的語言資訊。|

## <a name="remarks"></a>備註
 介面和 IDebugMemoryCoNtext2 介面之間的主要差異在於， `IDebugCodeContext2` [](../../../extensibility/debugger/reference/idebugmemorycontext2.md) `IDebugCodeContext2` 一律會對齊指令。 這表示 `IDebugCodeContext2` 一定會指向指示的開頭，而 `IDebugMemoryContext2` 可能會指向執行時間架構中的任何位元組記憶體。 `IDebugCodeContext2` 會以指示遞增，而不是基本的儲存體大小 (通常是位元組) 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
