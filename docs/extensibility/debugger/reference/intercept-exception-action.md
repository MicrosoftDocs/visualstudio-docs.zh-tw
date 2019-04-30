---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cac3e4fb6c072a26ede753213f6546c2ff50afa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914057"
---
# <a name="interceptexceptionaction"></a>INTERCEPT_EXCEPTION_ACTION
指定要攔截例外狀況時所採取的動作。

## <a name="syntax"></a>語法

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

#### <a name="parameters"></a>參數
IEA_INTERCEPT 可讓您攔截目前的例外狀況。 這是唯一支援目前的值，而且必須指定。

## <a name="remarks"></a>備註
這些值會傳遞至[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)方法。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
