---
title: IDebugEngine2::CauseBreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa0d559887019a697b820a5a6c91f80b78c6b713
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920955"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
其中一個其執行緒嘗試執行要求的所有程式進行偵錯此偵錯引擎 (DE) 來停止執行下一次。

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
 這個方法是非同步： [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)接下來，程式會嘗試將執行之後呼叫這個方法時，就會傳送事件。

## <a name="see-also"></a>另請參閱
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)