---
title: IDebugEngine3::SetAllExceptions |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetAllExceptions
helpviewer_keywords:
- IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33735e047f0ac0266648afd2ffb4de0cbc908a25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920916"
---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
這個方法會設定所有未處理的例外狀況的狀態。

## <a name="syntax"></a>語法

```cpp
HRESULT SetAllExceptions(
   EXCEPTION_STATE dwState
);
```

```csharp
int SetAllExceptions(
   enum_EXCEPTION_STATE dwState
);
```

#### <a name="parameters"></a>參數
 `dwState`

 [in]其中一個[EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)