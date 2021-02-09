---
title: IDebugThread2：： GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a8a7a4f041e2a38cf1e24e8cf156d3e595010b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893850"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
取得執行緒的名稱。

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
擴展傳回執行緒的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 取出的名稱一律是可顯示的名稱，而此名稱會描述該執行緒。 執行緒名稱可能衍生自支援命名執行緒的執行時間架構，也可能是衍生自 debug 引擎的名稱。 或者，您可以呼叫 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) 方法來設定執行緒的名稱。

## <a name="see-also"></a>另請參閱
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
