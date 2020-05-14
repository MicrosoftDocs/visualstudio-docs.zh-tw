---
title: IDebug攔截例外完成事件2::獲取攔截餅乾 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9065c0b7868efaeb70c10a3ab921a8764694662e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727785"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
當截獲的異常的處理完成時調用。

## <a name="syntax"></a>語法

```cpp
HRESULT GetInterceptCookie(
   UINT64* pqwCookie
);
```

```csharp
int GetInterceptCookie(
   out ulong pqwCookie
);
```

## <a name="parameters"></a>參數
`pqwCookie`\
[出]與被截獲的異常關聯的唯一值。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則返回錯誤代碼。

## <a name="remarks"></a>備註
 [攔截異常](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)方法完成對截取異常的處理后,它將發送[I攔截異常完成事件2。](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) 處理程式可以使用`GetInterceptCookie`方法 檢索與異常關聯的唯一值(`InterceptCurrentException`傳遞給 方法的相同值)。

## <a name="see-also"></a>另請參閱
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
