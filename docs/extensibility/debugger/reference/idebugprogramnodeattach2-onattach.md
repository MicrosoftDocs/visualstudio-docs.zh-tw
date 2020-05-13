---
title: IDebug程式節點附加2::上附加 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721871"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
附加到關聯的程式或延遲附加過程到[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。

## <a name="syntax"></a>語法

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>參數
`guidProgramId`\
[在]`GUID`分配給關聯的程式。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 如果`S_FALSE`不應調用[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法,則返回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 在調用[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法之前,在附加過程中調用此方法。 該方法`OnAttach`可以執行附加進程本身(在這種情況下,此`S_FALSE`方法返回)或將附加過程延遲`IDebugEngine2::Attach`到`OnAttach`方法( 該方法`S_OK`返回)。 在任一事件中,`OnAttach`該方法都可以將`GUID`正在除錯的程式設定為給`GUID`定的 。

## <a name="see-also"></a>另請參閱
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
