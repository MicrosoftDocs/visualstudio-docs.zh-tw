---
title: IDebug文檔位置2::獲取範圍 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731672"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
獲取此文件位置的範圍。

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
[進出]用起始位置填充[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

`pEndPosition`\
[進出]用結束位置填充[的TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 除錯引擎 (DE) 使用在位置斷點的文件位置中指定的範圍來提前搜尋實際貢獻代碼的語句。 例如，請參考下列程式碼：

```
Line 5: // comment
Line 6: x = 1;
```

 第 5 行對正在調試的程序沒有貢獻任何代碼。 如果在第 5 行上設置斷點的調試器希望 DE 向前搜索一定數量的第一行貢獻代碼,則調試器將指定一個範圍,其中包括可能正確放置斷點的其他候選行。 然後,DE 會向前搜索這些行,直到找到可以接受斷點的行。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
