---
title: IDebug符號搜索事件2::獲取符號搜索資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718894"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
由事件處理程式調用以檢索有關符號載入進程的結果。

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
[出]IDebugModule3 物件,表示為其載入符號的模組。

`pbstrDebugMessage`\
[進出]返回包含模組中任何錯誤消息的字串。 如果沒有錯誤,則此字串將僅包含模組的名稱,但它永遠不會為空。

> [!NOTE]
> [C++]`pbstrDebugMessage`無法,`NULL`必須釋放`SysFreeString`與 。

`pdwModuleInfoFlags`\
[出][MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)枚舉中的標誌的組合,指示是否載入了任何符號。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 當處理程式嘗試載入模組的調試符號後收到[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)事件時,處理程式可以調用此方法以確定該載入的結果。

## <a name="see-also"></a>另請參閱
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
