---
title: IDebugPortRequest2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724794"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
此介面描述埠。 此說明用於將埠添加到埠供應商。

## <a name="syntax"></a>語法

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 通常在從埠供應商獲取調試埠的過程中實現此介面。

## <a name="notes-for-callers"></a>通話備註
 此介面傳遞到[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)以創建除錯埠。 對[GetPortRequest 的](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)調用將返回此介面,表示最初用於創建埠的請求。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPortRequest2`。

|方法|描述|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|獲取要建立的埠的名稱。|

## <a name="remarks"></a>備註
 調試引擎通常不與埠供應商交互,並且對此介面沒有用處。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
