---
title: IDebugDocumentPositionOffset2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69fbdef70fc9c95ef571ce0ce796199292417ca0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933553"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
以字元位移表示原始檔中的位置。

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 由 IDE 所執行，並由 debug 引擎使用。

## <a name="methods"></a>方法
 下表顯示的方法 `IDebugDocumentPositionOffset2` 。

|方法|描述|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|抓取目前檔位置的範圍。|

## <a name="remarks"></a>備註
 這會傳回與 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) 相同的資訊，但會傳回 `char` 檔開頭的位移。 這會呈現像是存在於磁片上的檔，也就是一維的字元陣列，而不是通常會傳回的行和欄資訊。

## <a name="requirements"></a>規格需求
 標頭： Msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
