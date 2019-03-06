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
ms.openlocfilehash: 79385348aa9290f26a34b99dbd2d6f68cb92dc8a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680278"
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

#### <a name="parameters"></a>參數
 `pExceptionInfo`

 [in、 out][EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)會填入的例外狀況描述的結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註

 [只有 c + +]呼叫端負責釋放中的任何字串[EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)結構，以及釋放[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)結構中的物件。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)