---
title: IDebug程序發佈者2::Publish程序節點 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df68e72ee8597805bf02cb9c6e1c3a0bcaf8a449
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721675"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
使程式節點可供調試引擎 (DEs) 和會話調試管理器 (SDM) 使用。

## <a name="syntax"></a>語法

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>參數
`pProgramNode`\
[在][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件,表示要提供的程式節點。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法允許在選擇和啟動程式進行調試之前查詢程式以獲取資訊。

 要從可用性中刪除程式節點,請呼叫[「取消發佈程式節點」](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
