---
title: IDebugPort2 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725225"
---
# <a name="idebugport2"></a>IDebugPort2
此介面代表機器上的 debug 埠。

## <a name="syntax"></a>語法

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 自訂通訊埠供應商會執行此介面，以代表機器上的 debug 埠。

 如果埠支援傳送埠事件，它也必須執行 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 介面以支援 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 介面，進而提供 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) 或 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 的呼叫會傳回這個介面，代表所要求的埠。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPort2` 。

|方法|描述|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|傳回埠名稱。|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|傳回埠識別碼。|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|傳回用來建立埠 (（如果可用) ）的要求。|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|傳回此埠的埠供應商。|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|根據進程的識別碼，傳回進程的介面。|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|列舉在埠上執行的所有處理常式。|

## <a name="remarks"></a>備註
 本機埠可讓您存取在本機電腦上執行的所有處理常式和程式。 其他埠可能代表連至 Windows CE 型裝置的序列纜線連線，或是連至非 DCOM 電腦的網路連線。 `IDebugPort2`介面是用來尋找埠的名稱和識別碼，並列舉在埠上執行的所有處理常式。 在埠上啟動和終止進程的功能會在介面中執行 `IDebugPortEx2` 。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
