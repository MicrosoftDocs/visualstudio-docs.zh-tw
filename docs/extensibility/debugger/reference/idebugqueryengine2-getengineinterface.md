---
title: IDebug查詢引擎2::獲取引擎介面 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82f3214783a35e668bf3164c8659f60f863e9a43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720672"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
獲取自定義除錯引擎 (DE) 介面。

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

## <a name="parameters"></a>參數
`ppUnk`\
[出]返回一`IUnknown`個物件表示調試引擎 (DE),該物件可以查詢與 DE 關聯的任何其他有效介面(例如[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)或[IDebugEngine Launch2)。](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 生成的介面應謹慎使用,因為通過此方法檢索的介面調用會繞過會話調試管理器的處理,並可能導致 SDM 在調試時進入不良狀態或生成錯誤。

## <a name="see-also"></a>另請參閱
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
