---
title: IDebug 待定斷點2::綁定 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83d48e8df847620716b0f581be65ded48e2e5a13
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725983"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
將此掛起的斷點綁定到一個或多個代碼位置。

## <a name="syntax"></a>語法

```cpp
HRESULT Bind( 
   void 
);
```

```csharp
int Bind();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。 如果`E_BP_DELETED`斷點已被刪除,則返回。

## <a name="remarks"></a>備註
 呼叫此方法時,除錯引擎 (DE) 應嘗試將此掛起的斷點綁定到匹配的所有程式碼位置。

 此方法返回后,調用方需要等待指示掛起斷點已綁定或出錯的事件,然後再假定對[EnumBoundBreakpoint 或](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) [EnumErrorBreakpoint](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).方法的調用將分別枚舉所有綁定或錯誤斷點。

## <a name="see-also"></a>另請參閱
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
