---
title: IDebugProgramHost2::獲取主機名 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722226"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
取得此程式的託管過程的標題、友好名稱或檔名。

## <a name="syntax"></a>語法

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>參數
`dwType`\
[在][GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)枚舉中的值。

`pbstrHostName`\
[出]返回託管進程的請求名稱。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 在此方法的典型實現中,將忽略參數`dwType`,並返回主機的友好名稱。 另一個可能的實現是將`dwType`參數傳遞給[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法的調用以獲取名稱。

## <a name="see-also"></a>另請參閱
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
