---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d94a685b9c79069a047e32155234f9bf6a50d5c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875397"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
此介面代表變數的類型。

## <a name="syntax"></a>語法

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者會實作這個介面，可以在執行階段決定任何類型的基底類別。 這適用於 managed 程式碼。

## <a name="notes-for-callers"></a>呼叫端資訊
 此介面代表可從中衍生更具特製化的介面的基底類別。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面沒有提供任何方法以外繼承自`IDebugField`。

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)