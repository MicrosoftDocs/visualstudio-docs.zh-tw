---
title: IEnumDebugCode_s______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717278"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
此介面枚舉與調試會話或特定程式或文檔關聯的代碼上下文。

## <a name="syntax"></a>語法

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示程式中特定文本位置的程式碼上下文清單或特定文檔上下文的程式碼上下文清單。

## <a name="notes-for-callers"></a>通話備註
 呼叫[EnumCodeContext](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)以取得此介面,該介面表示程式源文件中特定文本位置的代碼上下文清單。

 呼叫[EnumCodeContext](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)以取得此介面,以表示特定原始文件中所有代碼上下文的清單。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugCodeContexts2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|檢索枚舉序列中指定數量的代碼上下文。|
|[跳](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|在枚舉序列中跳過指定數量的代碼上下文。|
|[重設](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|獲取枚舉器中的代碼上下文數。|

## <a name="remarks"></a>備註
 Visual Studio 呼叫[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)來填充使用者在設定下一個語句或顯示原始碼的拆解時可以選擇的代碼上下文清單。 例如,當C++範本有多個實例時,可能會發生多個代碼上下文。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
