---
title: IDebugBinder3::獲取所有別名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735816"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
此方法從程式中檢索別名清單。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>參數
`uRequest`\
[在]要返回的最大別名數(指定傳遞到`ppAliases`的陣列的長度。

`ppAliases`\
[進出]要用別名填充的陣列(如果這是空值,為`uRequest`0,則可以返回的別名計數將由`puFetched`返回返回。

`puFetched`\
[出]返回獲得的別名數。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
