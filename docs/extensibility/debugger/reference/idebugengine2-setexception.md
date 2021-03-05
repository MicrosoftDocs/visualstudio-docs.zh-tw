---
description: 指定 debug engine (DE) 應該如何處理指定的例外狀況。
title: IDebugEngine2：： SetException |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 543cccbbefd12accd75213f255f8e3b677cdea38
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153933"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
指定 debug engine (DE) 應該如何處理指定的例外狀況。

## <a name="syntax"></a>語法

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>參數
`pException`\
在描述例外狀況以及如何進行調試的 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 系統可能會指示您在第一次機會、第二次或完全不會產生例外狀況時，停止程式。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
