---
title: IDebugField：： GetSize |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6330179f1bbfffcb1f590dfc09ae0c06385f12e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869852"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
這個方法會取得欄位的大小（以位元組為單位）。

## <a name="syntax"></a>語法

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>參數
`pdwSize`\
擴展傳回大小。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 所有欄位都有類型，而且所有類型都有大小。 例如，具有 byte 類型的欄位大小為1個位元組。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
