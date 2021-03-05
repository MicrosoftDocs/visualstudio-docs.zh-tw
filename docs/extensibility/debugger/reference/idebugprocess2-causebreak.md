---
description: 要求在此進程中執行程式碼的下一個程式會終止，並傳送 IDebugBreakEvent2 事件物件。
title: IDebugProcess2：： CauseBreak |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28a4da4c0f7e4f8770478a47a73f7567506d5ae2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161394"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
要求在此進程中執行程式碼的下一個程式會終止，並傳送 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 事件物件。

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
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
