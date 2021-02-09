---
title: IDebugDisassemblyStream2：： GetCodeLocationId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8437dd2c98373c770d6f537e0ec9714100e3c4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901821"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
傳回特定程式碼內容的程式碼位置識別碼。

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
在要轉換成識別碼的 [IDebugCodeCoNtext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 物件。

`puCodeLocationId` 擴展傳回程序代碼位置識別碼。 請參閱＜備註＞。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。 `E_CODE_CONTEXT_OUT_OF_SCOPE`如果程式碼內容有效但超出範圍，則傳回。

## <a name="remarks"></a>備註
 程式碼位置識別碼專屬於 debug engine (DE) 支援反組解碼。 這個位置識別碼會由 DE 在內部使用，以追蹤程式碼中的位置，而且通常是某個位址或某種類型的位移。 唯一的要求是，如果某個位置的程式碼內容小於另一個位置的程式碼內容，則第一個程式碼內容的對應程式碼位置識別碼也必須小於第二個程式碼內容的程式碼位置識別碼。

 若要取出程式碼位置識別碼的程式碼內容，請呼叫 [GetCodeCoNtext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
