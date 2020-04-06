---
title: IDebug文檔位置偏移2::獲取範圍 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731622"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
檢索當前文檔位置的範圍。

## <a name="syntax"></a>語法

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>參數
`pdwBegOffset`\
[進出]範圍開始位置的偏移。 如果不需要此資訊,則此參數設定為 null 值。

`pdwEndOffset`\
[進出]範圍結束位置的偏移。 如果不需要此資訊,則此參數設定為 null 值。

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
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
