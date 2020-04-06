---
title: IDebugexception2::坎帕斯托調試點 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729878"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
確定除錯引擎 (DE) 是否支援在復原執行時將此異常傳遞給正在除錯的程式的選項。

## <a name="syntax"></a>語法

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>傳回值
 返回(`S_OK`異常可以傳遞給程式)`S_FALSE`或 (無法傳遞異常)。

## <a name="remarks"></a>備註
 DE 必須具有傳遞給調試器的預設操作。 IDE 可能會接收[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件,並在`CanPassToDebuggee`不調用 該方法的情況下調用["繼續"](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法。 因此,DE 應具有傳遞異常的默認情況。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
