---
title: IDebugThread2:獲取名稱 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718768"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
獲取線程的名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>參數
`pbstrName`\
[出]返回線程的名稱。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 檢索的名稱始終是可以顯示的名稱,此名稱描述線程。 線程名稱可能來自支援命名線程的運行時體系結構,或者可能是從調試引擎派生的名稱。 或者,線程的名稱可以通過調用[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)方法來設置。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
