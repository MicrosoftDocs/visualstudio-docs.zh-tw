---
title: IDebugProcess2::枚舉 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724065"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
檢索進程中運行的所有線程的清單。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
[出]返回包含進程中所有程式中所有線程的清單的[IEnum DebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法枚舉每個程式中運行的線程,然後將它們合併到線程的進程視圖中。 單個線程可能在多個程式中運行;但是,單個線程可能會在多個程式中運行。此方法僅枚舉該線程一次。

 此方法顯示行程線程的清單,而不重複。 否則,要枚舉在特定程式中運行的線程,請使用[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
