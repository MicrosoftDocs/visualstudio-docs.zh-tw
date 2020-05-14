---
title: IDebugField:等於 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729020"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
此方法將此欄位與指定的相等欄位進行比較。

## <a name="syntax"></a>語法

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>參數
`pField`\
[在]要與此比較的欄位。

## <a name="return-value"></a>傳回值
 如果欄位相同,則傳`S_OK`回 。 如果欄位不同,則返回"`S_FALSE.`否則",返回一個錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
