---
description: 告知程式或程式節點，debug engine (DE) 用來對此程式進行 debug 錯。
title: IDebugProgramEngines2：： SetEngine |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e938cd63c88d0d58866b36528a1342983dc457f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084177"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
告知程式或程式節點，debug engine (DE) 用來對此程式進行 debug 錯。

## <a name="syntax"></a>語法

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>參數
`guidEngine`\
在DE 的 GUID。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
