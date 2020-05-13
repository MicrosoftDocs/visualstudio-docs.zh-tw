---
title: IDebugProgramHost2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722219"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
此介面提供有關程式的主機(進程)資訊。

## <a name="syntax"></a>語法

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 調試引擎在[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面的同一對象上實現此介面,以提供有關託管過程的資訊。 這是一個可選的介面。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugProgram2`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProgramHost2`。

|方法|描述|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|取得此程式的託管過程的標題、友好名稱或檔名。|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|獲取此程式的託管進程的進程識別碼。|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|取得運行此程式的託管進程的電腦的名稱。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
