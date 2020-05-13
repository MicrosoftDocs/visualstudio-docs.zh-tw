---
title: IDebugAlias:獲取ICordebug值 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd01785fee7ce65296bac940fb19819415139d53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736486"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
檢索表示與此別名關聯的值的託管代碼介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>參數
`ppUnk`\
[出]`IUnknown`表示與此別名關聯的值的介面。 可以查詢介面的此`ICorDebugValue`介面。

## <a name="return-value"></a>傳回值
 如果成功,返回S_OK;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法僅適用於託管值(`ICorDebugValue`是 .NET 框架中可用的介面,並在 cordebug.idl 檔中的 .NET 框架 SDK 中定義)。

## <a name="see-also"></a>另請參閱
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
