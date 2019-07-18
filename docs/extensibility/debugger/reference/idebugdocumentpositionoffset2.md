---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3793d54249fca1dc867cfe4072326245a67852cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333264"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
表示原始程式檔中的字元位移的位置。

## <a name="syntax"></a>語法

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 IDE 所實作，而且由偵錯引擎。

## <a name="methods"></a>方法
 下表顯示的方法`IDebugDocumentPositionOffset2`。

|方法|描述|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|擷取目前的文件位置的範圍。|

## <a name="remarks"></a>備註
 這會傳回相同的資訊[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)但在`char`位移的文件的開頭。 例如，它會存在於磁碟上，也就是個字元，而不是正常情況下傳回行和資料行資訊的一維陣列，這會帶來文件。

## <a name="requirements"></a>需求
 標頭：Msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)