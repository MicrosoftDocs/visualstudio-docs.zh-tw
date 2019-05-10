---
title: IDebugPropertyCreateEvent2::GetDebugProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyCreateEvent2::GetDebugProperty
ms.assetid: d7e43183-444c-4417-af19-82e28229f83a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b953b18c96a48402e49f06443c09220d151204dd
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458802"
---
# <a name="idebugpropertycreateevent2getdebugproperty"></a>IDebugPropertyCreateEvent2::GetDebugProperty
取得新的屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>參數
 `ppProperty`\

 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示新屬性。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)