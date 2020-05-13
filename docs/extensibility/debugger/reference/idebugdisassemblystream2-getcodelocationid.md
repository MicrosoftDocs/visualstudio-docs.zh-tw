---
title: IDebugdisassemblystream2::獲取代碼定位Id |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32be70e11776177a0e68f09689c2262497703ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732248"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
返回特定代碼上下文的代碼位置識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>參數
`pCodeContext`\
[在]要轉換為識別碼的[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件。

`puCodeLocationId`[出]返回代碼位置識別碼。 請參閱＜備註＞。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_CODE_CONTEXT_OUT_OF_SCOPE`代碼上下文有效但超出範圍,請返回。

## <a name="remarks"></a>備註
 代碼位置識別碼特定於支援拆卸的調試引擎 (DE)。 此位置識別碼由 DE 在內部用於追蹤程式碼中的位置,通常是某種位址或偏移量。 唯一的要求是,如果一個位置的代碼上下文小於另一個位置的代碼上下文,則第一個代碼上下文的相應代碼位置標識符也必須小於第二個代碼上下文的代碼位置標識符。

 若要檢索代碼位置識別碼的程式碼上下文,請呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
