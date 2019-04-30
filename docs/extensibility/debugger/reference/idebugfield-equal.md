---
title: IDebugField::Equal |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed978355aa752730cfb43390b3e4b6f80d327f83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919461"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
這個方法會比較此欄位與指定欄位相等。

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

#### <a name="parameters"></a>參數
 `pField`

 [in]要與這個比較的欄位。

## <a name="return-value"></a>傳回值
 如果欄位是相同時，會傳回`S_OK`。 如果欄位不相同，就會傳回`S_FALSE.`否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)