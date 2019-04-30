---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0964c94334ca0815b4410f6858dca5502b2f8a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918152"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
設定服務提供者。

## <a name="syntax"></a>語法

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

#### <a name="parameters"></a>參數
 `pSP`

 [in]服務提供者的介面參考。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 任何其他方法之前呼叫，則會呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)