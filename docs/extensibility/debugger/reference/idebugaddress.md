---
description: 這個介面代表專案的位址。
title: IDebugAddress |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154960"
---
# <a name="idebugaddress"></a>IDebugAddress
這個介面代表專案的位址。 它是由符號處理常式傳回。

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會執行這個介面，以代表物件的位址。

## <a name="notes-for-callers"></a>呼叫者注意事項
 許多介面上的許多方法會傳回這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 此介面會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|抓取描述物件和其位置的 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 結構。|

## <a name="remarks"></a>備註
 符號提供者會傳回這個介面，以代表物件及其在特定範圍內的位置 (例如，函數、方法或類別) 。 這個介面會從傳回，並傳遞給符號提供者和運算式評估工具的各種方法。 通常，符號提供者是唯一需要解讀這個介面內容的實體。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
