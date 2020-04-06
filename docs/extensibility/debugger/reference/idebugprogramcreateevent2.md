---
title: IDebugProgram創建事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78088d6e5da61c32302c13b08143c9ed902452e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722636"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
此介面由除錯引擎 (DE) 連接到工作階段除錯管理員 (SDM) 時發送到工作階段除錯管理員 (SDM)。

## <a name="syntax"></a>語法

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 或自定義埠供應商實現此介面以報告已創建程式(通常在程式附加到程式時)。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現。 SDM`QueryInterface`使用方法`IDebugEvent2`存取介面。

## <a name="notes-for-callers"></a>通話備註
 DE 或自定義埠供應商創建並發送此事件物件以報告程式的創建。 DE 使用 SDM 在連接到正在除錯的程式時提供的[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔函數發送此事件。 自定義埠供應商使用[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面發送此事件。

## <a name="remarks"></a>備註
 DE 或自定義埠供應商通過調用[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)發佈新的[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
