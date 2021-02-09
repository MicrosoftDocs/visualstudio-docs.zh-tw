---
title: IDebugSymbolSearchEvent2：： GetSymbolSearchInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01b7ee4b0220fcd83573d29954c03d738ed53051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909374"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
由事件處理常式呼叫，以抓取符號載入進程的相關結果。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>參數
`pModule`\
擴展代表已載入符號之模組的 IDebugModule3 物件。

`pbstrDebugMessage`\
[in，out]傳回字串，其中包含模組中的任何錯誤訊息。 如果沒有錯誤，則此字串只會包含模組的名稱，但永遠不會是空的。

> [!NOTE]
> [C + +] `pbstrDebugMessage` 不能是 `NULL` ，而且必須使用來釋放 `SysFreeString` 。

`pdwModuleInfoFlags`\
擴展 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) 列舉中的旗標組合，指出是否已載入任何符號。

## <a name="return-value"></a>傳回值
 如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="remarks"></a>備註
 當處理常式在嘗試載入模組的偵錯工具符號之後收到 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 事件時，處理常式可以呼叫 thismethod 來判斷該載入的結果。

## <a name="see-also"></a>另請參閱
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
