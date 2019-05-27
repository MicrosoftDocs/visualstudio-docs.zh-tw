---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa6f4646894607823608b911c7a4e1df787fc05d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201131"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
取得引發這個事件的例外狀況的詳細的描述。

## <a name="syntax"></a>語法

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>參數
`pExceptionInfo`\
[in、 out][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)會填入的例外狀況描述的結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註

 [C++只]呼叫端負責釋放中的任何字串[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構，以及釋放[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)結構中的物件。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)