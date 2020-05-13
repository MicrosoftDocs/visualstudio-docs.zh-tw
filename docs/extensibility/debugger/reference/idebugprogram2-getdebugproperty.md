---
title: IDebugProgram2::獲取調試屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722888"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
獲取程式的屬性。

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
[出]返回表示程式屬性的[IDebug Property2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法返回的屬性特定於程式。 如果程式需要返回多個屬性,則此方法返回的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件是附加屬性的容器,調用[EnumSs 方法](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)返回所有屬性的清單。

 程式可能會公開可透過`IDebugProperty2`介面描述的任何數量和類型的其他屬性。 IDE 可能會透過通用屬性瀏覽器使用者介面顯示其他程序屬性。

## <a name="see-also"></a>另請參閱
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
