---
description: 從可用性中移除指定的程式節點， (DEs) 和會話 debug manager (SDM) 。
title: IDebugProgramPublisher2：： UnpublishProgramNode |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e3ee8b699fa73e6b8a8f4abc29624364f380add
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065134"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
從可用性中移除指定的程式節點， (DEs) 和會話 debug manager (SDM) 。

## <a name="syntax"></a>語法

```cpp
HRESULT UnpublishProgramNode(
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int UnpublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>參數
`pProgramNode`\
在代表要移除之程式節點的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 一旦移除之後，就無法再查詢程式的節點是否有程式資訊。

 若要讓程式節點可供使用，請呼叫 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
