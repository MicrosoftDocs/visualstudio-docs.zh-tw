---
title: IDebug動態場 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731309"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
此介面表示變數的類型。

## <a name="syntax"></a>語法

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由符號提供程式實現,作為可在運行時確定的任何類型的基類。 這僅適用於託管代碼。

## <a name="notes-for-callers"></a>通話備註
 此介面表示可以從中提取更專用的介面的基類。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面不提供除從`IDebugField`繼承的方法之外的任何其他方法。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
