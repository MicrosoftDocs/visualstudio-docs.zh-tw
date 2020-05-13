---
title: IDebugProcess2::終止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Terminate
helpviewer_keywords:
- IDebugProcess2::Terminate
ms.assetid: 5e6bf373-0fe9-4321-b04a-473a65f664d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8da1b2719e8b37df009e3bbef99e57c24117a963
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723812"
---
# <a name="idebugprocess2terminate"></a>IDebugProcess2::Terminate
終止進程。

## <a name="syntax"></a>語法

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 當行程終止時,該進程中的所有程序都終止;不允許再運行任何代碼。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
