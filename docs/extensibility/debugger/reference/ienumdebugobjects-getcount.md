---
title: IEnumDebugObjects：： GetCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1475652e340ff793dc900ab11563c0c1ad82c9b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716346"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
這個方法會傳回列舉中的元素數目。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
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
 這個方法不是慣例 COM 列舉介面的一部分，這會指定只需要執行 Next、Clone、Skip 和 Reset。

## <a name="see-also"></a>另請參閱
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
