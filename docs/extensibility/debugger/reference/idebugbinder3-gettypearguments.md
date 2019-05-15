---
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 164b6ca7fcfa71117060e5230cc9c9b3aeeb6c61
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614666"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
這個方法會擷取與這個物件相關聯的引數類型的清單。

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
[in]取得引數型別之前，要略過的欄位數目。

`count`\
[in]要傳回的引數欄位數目 (也會指定的大小`ppFields`陣列)。

`ppFields`\
[in、 out]將會填入這個方法傳回的欄位的陣列。

`pFetched`\
[out]\(選擇性)引數的數字輸入實際傳回的欄位。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 可以事先取得引數類型的數目，與[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)