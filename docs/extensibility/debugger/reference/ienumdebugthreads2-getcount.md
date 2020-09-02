---
title: IEnumDebugThreads2：： GetCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::GetCount
helpviewer_keywords:
- IEnumDebugThreads2::GetCount
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81c697c3b2121cb5cc59ebcd51f92f9a15cdc4b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715210"
---
# <a name="ienumdebugthreads2getcount"></a>IEnumDebugThreads2::GetCount
傳回列舉中的元素數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>參數
`pcelt`\
擴展傳回列舉中的元素數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法不是慣例 COM 列舉介面的一部分，它會指定只 `Next` `Clone` `Skip` 需要執行、、和 `Reset` 方法。

## <a name="see-also"></a>另請參閱
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
