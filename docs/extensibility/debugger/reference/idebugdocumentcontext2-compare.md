---
title: IDebugDocumentCoNtext2：： Compare |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 959d909d0c777110905aff3b11c8c29d27d628dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880758"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
將此檔內容與指定的檔內容陣列進行比較。

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
在 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 列舉中的值，指定比較的類型。

`rgpDocContextSet`\
在 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 物件的陣列，表示要比較的檔內容。

`dwDocContextSetLen`\
在要比較之檔內容陣列的長度。

`pdwDocContext`\
擴展傳回 `rgpDocContextSet` 符合比較之第一個檔內容陣列中的索引。

## <a name="return-value"></a>傳回值
 `S_OK`如果找到相符的，則傳回。 `S_FALSE`如果找不到相符項，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 陣列中所傳遞的 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 物件必須由相同的 debug 引擎（此引擎）實作為 `IDebugDocumentContext2` 正在呼叫的物件，否則比較是不正確。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
