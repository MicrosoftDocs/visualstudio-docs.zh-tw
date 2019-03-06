---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 611a3103c2747040ae9d72c53a905ee3f23c180a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688286"
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
包含的資料在程式碼的原始程式檔中的特定行中斷點的位置。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>成員
`bstrContext` 中斷點的內容，通常是呼叫堆疊上所示的方法或函式的名稱。

`pDocPos` [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)物件，表示文件位置的中斷點。

## <a name="remarks"></a>備註
此結構是隸屬[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的聯集的一部分。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
