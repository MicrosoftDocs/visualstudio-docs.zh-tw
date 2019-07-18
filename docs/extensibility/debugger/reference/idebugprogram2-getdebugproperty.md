---
title: IDebugProgram2::GetDebugProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 109e3ac1267afb4097429aafc9264416f3c2dbf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319361"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
取得程式的屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>參數
`ppProperty`\
[out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示程式的屬性。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的屬性專屬於該程式。 如果程式需要傳回多個屬性，則[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)這個方法所傳回的物件是一個容器的其他屬性，並呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法會傳回所有屬性的清單。

 程式可能會公開任意數目和類型的其他屬性，可透過描述`IDebugProperty2`介面。 IDE 可能會顯示透過泛型屬性瀏覽器使用者介面的其他程式屬性。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)