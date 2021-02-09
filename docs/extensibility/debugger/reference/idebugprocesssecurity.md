---
title: IDebugProcessSecurity |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c6807ff64d8acf44551fa12fcb79199d3817373
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933020"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` 由埠供應商執行，以警告附加至進程的使用者是不安全的。

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugProcessSecurity` 。

|方法|描述|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|從埠供應商取得使用者名稱。|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|警告附加至偵錯工具的使用者是不安全的。|

## <a name="remarks"></a>備註
 執行此介面以顯示警告，並允許使用者在您附加的進程被視為不安全時取消。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [連接埠](../../../extensibility/debugger/ports.md)
- [連接埠提供者](../../../extensibility/debugger/port-suppliers.md)
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
