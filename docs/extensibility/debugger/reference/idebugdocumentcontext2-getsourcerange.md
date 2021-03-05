---
description: 取得此檔內容的原始程式碼範圍。
title: IDebugDocumentCoNtext2：： GetSourceRange |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d02dfbd93002bedadd4c82168d498f89050ddc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162897"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
取得此檔內容的原始程式碼範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>參數
`pBegPosition`\
[in，out]以開始位置填入的 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 結構。 如果不需要這項資訊，請將此引數設定為 null 值。

`pEndPosition`\
[in，out]以結束位置填滿的 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 結構。 如果不需要這項資訊，請將此引數設定為 null 值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 來源範圍是整個範圍的原始程式碼，從目前的語句，再到提供程式碼的上一個語句之後。 來源範圍通常用於在 [反組解碼] 視窗中混合來源語句（包括批註）和程式碼。

 若要取得僅包含在此檔內容中之程式碼語句的範圍，請呼叫 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
