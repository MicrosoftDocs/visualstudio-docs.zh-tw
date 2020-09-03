---
title: IEnumDebugAddresses：： Reset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48026ee5f359c80c2c807fa857f1ec749823e2b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717632"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
這個方法會將列舉重設為第一個元素。

## <a name="syntax"></a>語法

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>參數
 無

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法之後， [下一次](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) 呼叫會傳回列舉的第一個元素。

## <a name="see-also"></a>另請參閱
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [下一個](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
