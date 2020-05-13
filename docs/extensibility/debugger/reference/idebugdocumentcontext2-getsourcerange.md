---
title: IDebug文檔上下文2::獲取來源範圍 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731795"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
獲取此文件上下文的原始程式碼範圍。

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
[進出]用起始位置填充[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

`pEndPosition`\
[進出]用結束位置填充[的TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構。 如果不需要此資訊,則此參數設定為 null 值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 源範圍是原始碼的整個範圍,從當前語句回回,到上次提供代碼的語句之後。 源範圍通常用於將源語句(包括註釋)與拆解視窗中的代碼混合。

 要取得本文件上下文中包含的代碼語句的範圍,請調用[Get語句範圍](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
