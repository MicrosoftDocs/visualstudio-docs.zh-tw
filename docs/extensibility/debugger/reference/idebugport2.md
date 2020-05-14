---
title: IDebugPort2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725225"
---
# <a name="idebugport2"></a>IDebugPort2
此介面表示電腦上的調試埠。

## <a name="syntax"></a>語法

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 自定義埠供應商實現此介面以表示電腦上的調試埠。

 如果埠支援發送埠事件,它還必須實現<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面以支援介面,該<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面反過來提供[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。

## <a name="notes-for-callers"></a>通話備註
 對[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)或[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)的調用返回此介面,表示請求的埠。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPort2`。

|方法|描述|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|返回埠名稱。|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|返回埠標識碼。|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|返回用於創建埠的請求(如果可用)。|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|返回此埠的埠供應商。|
|[抓取程序](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|返回進程介面,給定進程的標識符。|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|枚舉在埠上運行的所有進程。|

## <a name="remarks"></a>備註
 本地埠提供對本地電腦上運行的所有進程和程式的訪問。 其他埠可能表示與基於 Windows CE 的裝置的串列電纜連接,或與非 DCOM 電腦的網路連接。 介面`IDebugPort2`用於查找埠的名稱和標識符,並枚舉在埠上運行的所有進程。 在`IDebugPortEx2`介面中實現了在埠上啟動和終止進程的設施。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
