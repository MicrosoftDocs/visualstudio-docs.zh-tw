---
title: IDebugBinder3::獲取類型參數 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7667b06348c5e1b2865b24ab49095772808d6c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735697"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
此方法檢索與此物件關聯的參數類型的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>參數
`skip`\
[在]取得參數類型之前要跳過的欄位數。

`count`\
[在]要返回的參數位段數(也指定`ppFields`數位的大小)。

`ppFields`\
[進出]返回此方法時將填充的欄位陣列。

`pFetched`\
[出]\(可選) 實際傳回的參數型態欄位數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 可以使用[GetType參數計數](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)提前獲取參數類型的數量。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
