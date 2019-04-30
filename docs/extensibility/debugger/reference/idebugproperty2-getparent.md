---
title: IDebugProperty2::GetParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30fa28ba52d40698447c6607be4b694466bb6127
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916641"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
取得屬性的父屬性。

## <a name="syntax"></a>語法

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

#### <a name="parameters"></a>參數
 `ppParent`

 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示屬性的父代。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_GETPARENT_NO_PARENT`如果沒有父系。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)