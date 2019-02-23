---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5ac40af5f508a00b010025f9851ee2a8933dfa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720964"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
取得自訂的偵錯引擎 (DE) 介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

#### <a name="parameters"></a>參數
 `ppUnk`

 [out]傳回`IUnknown`物件代表偵錯引擎 (DE)，以及可查詢的其他規定與相關聯的有效介面 (例如[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)或是[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md))。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 應該謹慎使用產生的介面，因為透過擷取自這個方法的介面呼叫規避工作階段偵錯管理員的處理，而且可能會導致 SDM 進入錯誤狀態，或在偵錯時產生錯誤。

## <a name="see-also"></a>另請參閱
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)