---
title: IEEVisualizerService::GetPropertyProxy |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetPropertyProxy
helpviewer_keywords:
- IEEVisualizerService::GetPropertyProxy method
ms.assetid: 748750f4-76e7-4580-9da2-afba07681b37
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64a05032118588679efcc455953b76227a973319
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225862"
---
# <a name="ieevisualizerservicegetpropertyproxy"></a>IEEVisualizerService::GetPropertyProxy
這個方法傳回的屬性物件的 proxy。

## <a name="syntax"></a>語法

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>參數
 `dwID`\

 [in]要擷取的屬性 proxy 的識別碼。

 `proxy`\

 [out]需要 proxy 中實作[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)要求傳遞至這個方法為其支援一部分類型視覺化檢視。

## <a name="see-also"></a>另請參閱
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)