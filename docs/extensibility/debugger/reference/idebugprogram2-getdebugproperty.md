---
title: IDebugProgram2：： GetDebugProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb0bb520d3a821d777d5deaeaa200c4b7e526f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911964"
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
擴展傳回代表程式屬性的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 這個方法所傳回的屬性是程式特有的屬性。 如果程式需要傳回一個以上的屬性，則這個方法所傳回的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 物件會是其他屬性的容器，而呼叫 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 方法會傳回所有屬性的清單。

 程式可能會公開可透過介面描述的任何其他屬性數目和類型 `IDebugProperty2` 。 IDE 可能會透過一般的屬性瀏覽器使用者介面來顯示其他程式屬性。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
