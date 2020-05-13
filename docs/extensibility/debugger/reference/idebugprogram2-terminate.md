---
title: IDebugProgram2::終止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722754"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
終止程式。

## <a name="syntax"></a>語法

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 如果可能,程式將被終止並從行程卸載;否則,調試引擎 (DE) 將執行任何必要的清理。

 此方法或[終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)方法由IDE調用,通常是回應使用者停止所有調試。 理想情況下,此方法的實現應在進程中終止程式。 如果這是不可能的,DE 應阻止程式在此進程中再運行任何(並進行任何必要的清理)。 如果`IDebugProcess2::Terminate`IDE 調用了該方法,則整個進程將在`IDebugProgram2::Terminate`調用 該方法後的某個時間終止。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
