---
title: IDebugClassField：： EnumInterfacesImplemented |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734482"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
為這個類別所執行的介面建立枚舉器。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>參數
`ppEnum`\
擴展傳回 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 物件，這個物件代表所實的介面清單。 如果沒有任何介面，則會傳回 null 值。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK，如果沒有在這個類別上執行任何介面，則傳回 S_FALSE。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 列舉的每個元素都是描述介面的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 物件。 請注意，非受控程式 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 代碼不會使用介面做為離散實體，因此這個方法一律會傳回非受控碼的 null 值 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 。

## <a name="see-also"></a>另請參閱
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
