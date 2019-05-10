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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9248ad59a564207befb0b0a3ff1c229840ee336b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457721"
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

## <a name="parameters"></a>參數
 `ppRererence`\

 [out]傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，表示屬性的值的參考。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回的錯誤代碼，通常`E_NOTIMPL`或`E_GETREFERENCE_NO_REFERENCE`。

## <a name="see-also"></a>另請參閱
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)