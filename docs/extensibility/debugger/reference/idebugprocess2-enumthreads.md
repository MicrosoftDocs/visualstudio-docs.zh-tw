---
description: 抓取在進程中執行之所有線程的清單。
title: IDebugProcess2：： EnumThreads |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c502504b3a31f3e4689db34f907f9596b214877
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071606"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
抓取在進程中執行之所有線程的清單。

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
擴展傳回 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) 物件，其中包含進程中所有程式內所有線程的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法會列舉在每個程式中執行的執行緒，然後將它們合併到執行緒的進程視圖中。 單一線程可能會在多個程式中執行;這個方法只會列舉該執行緒一次。

 這個方法會顯示進程的執行緒清單，而不會有重複的專案。 否則，若要列舉在特定程式中執行的執行緒，請使用 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
