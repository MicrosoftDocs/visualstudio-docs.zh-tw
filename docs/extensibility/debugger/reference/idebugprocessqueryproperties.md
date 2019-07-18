---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ddb98c2d7e63fc27ad1469dfbfc76eaaee38582
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353107"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
這個介面是藉由將延伸模組介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)實作者。 它可讓實作者，以取得有關偵錯的處理序環境。

## <a name="syntax"></a>語法

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 實作這個介面，以取得有關偵錯程序的執行環境。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcessQueryProperties`。

|方法|描述|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|屬性值的查詢。|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|如需屬性值的查詢。|

## <a name="remarks"></a>備註
 很少會實作這個介面。

## <a name="requirements"></a>需求
 標頭：Portpriv.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)