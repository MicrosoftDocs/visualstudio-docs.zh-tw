---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a08ee3f637b954d2df7e48fb8f6aebbdd0948c19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414068"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面會提供存取型別、 別名和自訂視覺化檢視服務。

## <a name="syntax"></a>語法

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎會實作這個介面來支援別名、 自訂視覺化檢視服務和物件型別資訊的存取權。

## <a name="notes-for-callers"></a>呼叫端資訊
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面取得此介面使用[QueryInterface](/cpp/atl/queryinterface)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 所提供的方法除了[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面，這個介面會實作下列：

|方法|描述|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|擷取記憶體物件，表示這個物件所繫結的記憶體。|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|擷取此物件 （如果有的話），相關聯的例外狀況|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|擷取指定其名稱、 別名|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|擷取所有的別名，對此物件的陣列|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|取得與這個物件相關聯的引數類型的數目|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|擷取這個物件相關聯的引數類型的清單|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|取得視覺化檢視服務的介面|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|將記憶體內容的物件位置或 64 位元記憶體位址。|

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)