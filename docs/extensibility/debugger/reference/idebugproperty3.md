---
title: IDebugProperty3 |Microsoft Docs
description: 這個介面支援抓取與屬性相關聯的任意長字串、將唯一識別碼與屬性產生關聯、取得屬性的自訂檢視器清單、設定屬性值以及報告任何產生錯誤的能力。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 933810ac5b1e0ba34edf7cfe8d4303180c862fe2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083904"
---
# <a name="idebugproperty3"></a>IDebugProperty3
此介面提供下列支援：

- 正在抓取與屬性相關聯的任意長字串。

- 將唯一識別碼與屬性產生關聯。

- 正在抓取屬性的自訂檢視器清單。

- 設定屬性的值，使其能夠報告任何產生的錯誤

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會在執行 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 的相同物件上執行這個介面，以提供長字串、屬性識別碼和自訂檢視器的支援。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫介面上的 [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty2` 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自的方法之外 `IDebugProperty2` ，介面也會 `IDebugProperty3` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|傳回與屬性相關聯之字串的長度。|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|傳回使用者提供的緩衝區中的字串。|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|建立這個屬性的唯一識別碼。|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|終結這個屬性的唯一識別碼。|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|傳回可以用來查看此屬性的自訂檢視器數目。|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|傳回可以用來查看此屬性的自訂檢視器清單。|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|設定這個屬性的值，如果發生任何錯誤，則傳回錯誤訊息。|

## <a name="remarks"></a>備註
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 是會話 debug MANAGER (SDM) 設定屬性值的慣用方式。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
