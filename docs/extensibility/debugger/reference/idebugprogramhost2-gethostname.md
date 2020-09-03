---
title: IDebugProgramHost2：： GetHostName |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722226"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
取得此程式之裝載進程的標題、易記名稱或檔案名。

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
在 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 列舉中的值。

`pbstrHostName`\
擴展傳回裝載進程的要求名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 在此方法的一般執行中， `dwType` 會忽略參數，並傳回主機電腦的易記名稱。 另一種可能的實現方式是將 `dwType` 參數傳遞至 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) 方法的呼叫，以取得名稱。

## <a name="see-also"></a>另請參閱
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
