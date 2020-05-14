---
title: IDebugEngine2::刪除設置異常 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730930"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
刪除指定的異常,以便調試引擎不再處理它。

## <a name="syntax"></a>語法

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>參數
`pException`\
[在]描述要刪除的異常[EXCEPTION_INFO結構。](../../../extensibility/debugger/reference/exception-info.md)

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 要刪除的異常以前必須由對[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)方法的較早調用設置。

 要立即刪除所有設置的異常,請調用[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
