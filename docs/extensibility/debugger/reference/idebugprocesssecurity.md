---
title: IDebugProcess安全性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723184"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`由埠供應商實施,以警告使用者附加到進程不安全。

## <a name="syntax"></a>語法

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcessSecurity`。

|方法|描述|
|------------|-----------------|
|[取得使用者名稱](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|從埠供應商獲取使用者名。|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|警告使用者附加到調試過程不安全。|

## <a name="remarks"></a>備註
 實現此介面以顯示警告,並允許使用者取消,如果您要附加到的進程可能被視為不安全。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [連接埠](../../../extensibility/debugger/ports.md)
- [連接埠提供者](../../../extensibility/debugger/port-suppliers.md)
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
