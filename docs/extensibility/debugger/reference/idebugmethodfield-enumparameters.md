---
description: 建立方法參數的列舉值。
title: IDebugMethodField：： Microsoft.sqlserver.replication.agentprofile.enumparameters |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0f2085b6a2aff6b41456f47a01c446b1c646f353
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058387"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
建立方法參數的列舉值。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>參數
`ppParams`\
擴展傳回 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件，代表方法的參數清單。否則，如果沒有任何參數，則會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有任何參數，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 每個元素都是代表不同類型之參數的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。 在每個物件上呼叫 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 方法，以判斷該物件代表的參數類型。

 參數包含其變數名稱及其類型。 類別方法的第一個參數通常是 "this" 指標。

 如果只需要參數的類型，請呼叫 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
