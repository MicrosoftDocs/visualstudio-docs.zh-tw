---
title: IDebugGenericFieldDefinition：： ConstructInstantiation |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ab91340c0f9baf9a75e6e283d3c1158bdbea3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911115"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
在給定型別引數的陣列時，建立欄位實例。

## <a name="syntax"></a>語法

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>參數
`cArgs`\
在陣列中的引數數目 `ppArgs` 。

`ppArgs`\
在包含型別引數的陣列。 型別引數必須是封閉式類型 (非泛型或完全具現化的泛型) 。

`ppConstructedField`\
擴展傳回代表新欄位的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 不會檢查條件約束。

## <a name="see-also"></a>另請參閱
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
