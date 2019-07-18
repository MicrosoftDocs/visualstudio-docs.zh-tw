---
title: IDebugProgram2::CauseBreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a01b5982b4f747bd70c3a35bc0b7191bb54cd21b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311350"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
程式停止執行下一個要求的時間執行其執行緒嘗試的其中一個。

## <a name="syntax"></a>語法

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)接下來，程式會嘗試將執行程式碼之後會呼叫這個方法, 時，就會傳送事件。

 這個方法是非同步方法會立即傳回而不一定會等候程式停止。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)