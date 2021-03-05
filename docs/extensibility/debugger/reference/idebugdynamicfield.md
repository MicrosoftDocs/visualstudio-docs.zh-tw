---
description: 此介面代表變數的類型。
title: IDebugDynamicField |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcf148294a7c18c2b717bb4de63dac7e656e25d6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167226"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
此介面代表變數的類型。

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 此介面是由符號提供者實作為可在執行時間決定之任何類型的基類。 這僅適用于 managed 程式碼。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面代表基類，可從中衍生更特製化的介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 這個介面不提供繼承自的任何方法 `IDebugField` 。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
