---
title: IDebug文檔上下文2::比較 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731889"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
將此文件上下文與給定的文檔上下文陣列進行比較。

## <a name="syntax"></a>語法

```cpp
HRESULT Compare( 
   DOCCONTEXT_COMPARE       compare,
   IDebugDocumentContext2** rgpDocContextSet,
   DWORD                    dwDocContextSetLen,
   DWORD*                   pdwDocContext
);
```

```csharp
int Compare( 
   enum_ DOCCONTEXT_COMPARE compare,
   IDebugDocumentContext2[] rgpDocContextSet,
   uint                     dwDocContextSetLen,
   out uint                 pdwDocContext
);
```

## <a name="parameters"></a>參數
`compare`\
[在][DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)枚舉中指定比較類型的值。

`rgpDocContextSet`\
[在][IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件的陣列,表示要比較的文檔上下文。

`dwDocContextSetLen`\
[在]要比較的文檔上下文陣列的長度。

`pdwDocContext`\
[出]將索引返回到滿足比較`rgpDocContextSet`的第一個文檔上下文的陣列中。

## <a name="return-value"></a>傳回值
 如果`S_OK`找到匹配項,則返回。 如果`S_FALSE`未找到匹配項,則返回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列中傳遞的[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件必須由實現所呼叫物件的`IDebugDocumentContext2`同一調試引擎實現;否則,比較無效。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
