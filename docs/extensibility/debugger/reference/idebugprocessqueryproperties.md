---
title: IDebug行程查詢屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723286"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
此介面是由[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)實現者實現的擴展介面。 它允許實現者獲取有關調試過程環境的資訊。

## <a name="syntax"></a>語法

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 實現此介面以獲取有關調試過程的執行環境的資訊。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugProcessQueryProperties`。

|方法|描述|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|屬性值的查詢。|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|屬性值的查詢。|

## <a name="remarks"></a>備註
 此介面很少實現。

## <a name="requirements"></a>需求
 標題: 波特普里夫.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
