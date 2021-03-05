---
description: 這個方法會比較此欄位與指定的欄位是否相等。
title: IDebugField：：等於 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2bf9b3e4bbb988621e3b65e855b07322fba1795
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152087"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
這個方法會比較此欄位與指定的欄位是否相等。

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
在要與此一比較的欄位。

## <a name="return-value"></a>傳回值
 如果欄位相同，則會傳回 `S_OK` 。 如果欄位不同，則會傳回 `S_FALSE.` ，否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
