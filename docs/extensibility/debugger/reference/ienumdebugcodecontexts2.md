---
title: IEnumDebugCodeCoNtexts2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7dee04516d8bc8d72859509a9f721455d858a433
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929390"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
這個介面會列舉與 debug 會話相關聯的程式碼內容，或是與特定程式或檔相關聯的程式碼內容。

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表程式中特定文字位置的程式碼內容清單，或特定檔內容的程式碼內容清單。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumCodeCoNtexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 來取得這個介面，此介面代表程式之來源文件中特定文字位置的程式碼內容清單。

 呼叫 [EnumCodeCoNtexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) 以取得這個介面，此介面代表特定來源文件中的所有程式碼內容清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugCodeContexts2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|抓取列舉序列中指定數目的程式碼內容。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|略過列舉序列中指定數目的程式碼內容。|
|[重設](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|取得列舉值中的程式碼內容數目。|

## <a name="remarks"></a>備註
 Visual Studio 會呼叫 [EnumCodeCoNtexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) ，以填入使用者在設定下一個語句或顯示來源檔案的反組解碼時，可從中選擇的程式碼內容清單。 例如，當有多個 c + + 樣式範本的實例時，可能會發生多個程式碼內容。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
