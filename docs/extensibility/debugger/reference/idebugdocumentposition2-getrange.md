---
title: IDebugDocumentPosition2：： GetRange |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0a08889507c03ec1a8c5c72a615edfb195e7d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946848"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
取得此檔位置的範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
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
 偵錯工具引擎會使用位置中斷點的檔位置所指定的範圍 (DE) 來向前搜尋實際提供程式碼的語句。 例如，請參考下列程式碼：

```
Line 5: // comment
Line 6: x = 1;
```

 第5行對要進行調試的程式沒有任何程式碼。 如果在第5行設定中斷點的偵錯工具想要取消搜尋提供程式碼的第一行，偵錯工具會指定一個範圍，其中包含可能正確放置中斷點的其他候選行。 然後，會向前搜尋這些行，直到找到可接受中斷點的行為止。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
