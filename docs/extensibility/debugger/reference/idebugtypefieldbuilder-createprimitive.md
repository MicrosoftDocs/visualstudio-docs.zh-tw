---
title: IDebugTypeFieldBuilder：： CreatePrimitive |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePrimitive
- IDebugTypeFieldBuilder::CreatePrimitive
ms.assetid: 512c6ff0-97c5-409f-939f-4cc969bc4bb9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1f7601d2533a52fdee709413a97d203a6556cb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965716"
---
# <a name="idebugtypefieldbuildercreateprimitive"></a>IDebugTypeFieldBuilder::CreatePrimitive
建立代表基本類型的物件。

## <a name="syntax"></a>語法

```cpp
HRESULT CreatePrimitive (
   DWORD          dwElementType,
   IDebugField ** pTypeField
);
```

```csharp
int CreatePrimitive (
   uint            dwElementType,
   out IDebugField pTypeField
);
```

## <a name="parameters"></a>參數
`dwElementType`\
在 [CorElementType 列舉](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) 中的值，表示基本類型。

`pTypeField`\
擴展傳回新型別的 IDebugField 介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
