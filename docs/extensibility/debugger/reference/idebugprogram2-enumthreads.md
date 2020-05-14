---
title: IDebugProgram2::枚舉 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumThreads
helpviewer_keywords:
- IDebugProgram2::EnumThreads
ms.assetid: 0f2a8c51-1315-4c96-8aa1-6a937dc2a769
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76b93ef5489e57f74c05e5925b4304f1e93e9830
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722992"
---
# <a name="idebugprogram2enumthreads"></a>IDebugProgram2::EnumThreads
檢索程式中正在運行的線程的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumThreads( 
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads( 
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回包含線程清單的[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
