---
title: IEnumCodePaths2：： GetCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::GetCount
helpviewer_keywords:
- IEnumCodePaths2::GetCount
ms.assetid: 988c5092-fcc5-43a1-a94c-c261edd56ebf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab16a27257229bf97145403b99af9e478eae65db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717832"
---
# <a name="ienumcodepaths2getcount"></a>IEnumCodePaths2::GetCount
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
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
