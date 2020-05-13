---
title: IDebugCoreServer3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732815"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
此介面允許訪問有關進程運行中的伺服器的資訊。

## <a name="syntax"></a>語法

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>實施者說明
 可視化工作室實現此介面。

## <a name="notes-for-callers"></a>通話備註
 使用[查詢介面](/cpp/atl/queryinterface)從[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面獲取此介面。 對[GetServer 的](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)調用也可以返回此介面。 此介面最常由自訂埠供應商用於在伺服器上啟動程式(本地或遠端)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[取得伺服器名稱](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|檢索伺服器的名稱。|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|檢索伺服器名稱的友好版本|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|告訴特定的調試引擎在這些進程啟動時自動附加到進程。|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|自動附加失敗時檢索特定的錯誤代碼。|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|在伺服器上創建調試引擎的實例。|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|檢索指示伺服器是否與調用方位於同一台電腦上的標記。|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|檢索指示用於與伺服器通信的協議的值。|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|禁用此伺服器知道的所有調試引擎的所有自動附加設置。|

## <a name="remarks"></a>備註
 自定義埠供應商在調用[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)時接收[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面。 可以從`IDebugCoreServer3`該介面獲取介面。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
