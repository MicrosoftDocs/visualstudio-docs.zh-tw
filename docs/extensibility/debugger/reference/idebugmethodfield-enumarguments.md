---
title: IDebugMethodField：： EnumArguments |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b86fbdb87c0191ea8b43c64a542c37177a8ef1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900193"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
針對呼叫方法所需的每個引數，建立其類型的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>參數
`ppParams`\
擴展傳回代表引數類型清單的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件。 如果沒有引數，則傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有任何引數，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是代表每個參數類型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。 呼叫 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法來取得每個參數類型的相關資訊。

 如果需要參數的名稱以及型別，則呼叫 [microsoft.sqlserver.replication.agentprofile.enumparameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
