---
description: 抓取物件，該物件表示新建立的 debug engine (DE) 。
title: IDebugEngineCreateEvent2：： GetEngine |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2::GetEngine
helpviewer_keywords:
- IDebugEngineCreateEvent2::GetEngine
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aaabac0b9ee0e6fb2e8982d673e8e55e1cede4e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153663"
---
# <a name="idebugenginecreateevent2getengine"></a>IDebugEngineCreateEvent2::GetEngine
抓取物件，該物件表示新建立的 debug engine (DE) 。

## <a name="syntax"></a>語法

```cpp
HRESULT GetEngine( 
   IDebugEngine2** pEngine
);
```

```csharp
int GetEngine( 
   out IDebugEngine2 pEngine
);
```

## <a name="parameters"></a>參數
`pEngine`\
擴展傳回代表新建立之 DE 的 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
