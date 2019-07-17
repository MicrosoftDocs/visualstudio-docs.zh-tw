---
title: IEnumDebugProcesses2::Skip |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d61f20e0727870e706d63fe0467f6dfa0083c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179145"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
略過指定的元素數目。

## <a name="syntax"></a>語法

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

#### <a name="parameters"></a>參數
 `celt`

 [in]略過的項目數目。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 會傳回`S_FALSE`如果`celt`大於其餘項目數目，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 如果`celt`指定的值大於其餘的項目，列舉型別設定為結束和`S_FALSE`會傳回。

## <a name="see-also"></a>另請參閱
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)