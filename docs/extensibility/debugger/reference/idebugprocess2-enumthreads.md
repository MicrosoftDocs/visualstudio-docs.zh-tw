---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 664f4264fd12106fef0650a31a888470e09a3154
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353173"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
擷取處理序中執行的所有執行緒的清單。

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
[out]傳回[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)物件，其中包含一份程序中的所有程式 中的所有執行緒。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會列舉在每個程式中執行的執行緒，然後將它們合併成一個執行緒的處理序 檢視。 單一執行緒可以執行多個程式;這個方法會列舉該執行緒一次。

 這個方法會顯示一份不重複的處理程序的執行緒。 否則，若要列舉在特定的程式中執行的執行緒，請使用[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)