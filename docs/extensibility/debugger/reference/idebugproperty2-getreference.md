---
title: IDebugProperty2::GetReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abff655b41dbc55735b7dea2934f7d396aae5f4c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698114"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
傳回屬性的值的參考。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

#### <a name="parameters"></a>參數
 `ppRererence`

 [out]傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示屬性的值的參考。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回的錯誤代碼，通常`E_NOTIMPL`或`E_GETREFERENCE_NO_REFERENCE`。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)