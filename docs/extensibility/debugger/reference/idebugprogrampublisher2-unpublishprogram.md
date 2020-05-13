---
title: IDebug程序發佈者2::取消發佈程式 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721595"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
使程式無法調試。

## <a name="syntax"></a>語法

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>參數
`pDebuggeeInterface`\
[在]程序`IUnknown`的介面。 這是提供給[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)方法的值,唯一標識要刪除的程式(即用作 Cookie)。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 要使程式可供調試引擎和會話調試管理器使用,請使用[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
