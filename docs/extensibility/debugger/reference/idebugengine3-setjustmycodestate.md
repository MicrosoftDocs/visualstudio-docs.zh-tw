---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82c2834e7c368776f0ae91cf9106ec6331eed997
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920900"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
這個方法會告知偵錯引擎的 JustMyCode 狀態資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

#### <a name="parameters"></a>參數
 `fUpdate`

 [in]非零值 (`TRUE`) 來更新目前的資訊，請為零 (`FALSE`) 重設 （忽略任何先前設定） 的所有資訊。

 `dwModules`

 [in]中的資訊結構數目 `rgJMCSpec.`

 `rgJMCSpec`

 [in]陣列[JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)若要使用的結構。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 JustMyCode 是屬於使用者程式碼偵錯，並忽略所有的中繼程式碼，例如系統程式碼的概念，即使原始程式碼是適用於該系統程式碼。

## <a name="see-also"></a>另請參閱
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)