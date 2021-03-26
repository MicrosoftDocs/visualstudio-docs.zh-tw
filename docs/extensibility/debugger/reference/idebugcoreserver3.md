---
description: 這個介面可讓您存取執行進程之伺服器的相關資訊。
title: IDebugCoreServer3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab605db6a49b8b7cc9893692ff1bb9e6da15171f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088142"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
這個介面可讓您存取執行進程之伺服器的相關資訊。

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 使用 [QueryInterface](/cpp/atl/queryinterface) 從 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 介面取得這個介面。 對 [teamfoundationserverfactory.getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 的呼叫也可以傳回這個介面。 自訂埠供應商最常使用此介面，在伺服器上啟動程式 (本機或遠端) 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|抓取伺服器的名稱。|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|抓取伺服器名稱的易記版本|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|告知特定的偵錯工具引擎在這些處理常式啟動時自動附加至進程。|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|當自動附加失敗時，會抓取特定的錯誤碼。|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|在伺服器上建立 debug 引擎的實例。|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|抓取旗標，指出伺服器是否與呼叫端位於同一部電腦上。|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|抓取值，指出用來與伺服器通訊的通訊協定。|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|針對此伺服器所知道的所有偵錯工具引擎停用所有自動附加設定。|

## <a name="remarks"></a>備註
 自訂埠供應商會在呼叫[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)時收到[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面。 您 `IDebugCoreServer3` 可以從該介面取得介面。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
