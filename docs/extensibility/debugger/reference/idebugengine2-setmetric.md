---
title: IDebugEngine2::SetMetric |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 325cd30a49fb636c56eebd9e6301b3999e851363
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713603"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
這個方法會設定登錄值，稱為度量。

## <a name="syntax"></a>語法

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

#### <a name="parameters"></a>參數
 `pszMetric`

 [in]計量的名稱。

 `varValue`

 [in]指定度量的值。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 計量就是用來變更偵錯引擎的行為，或廣告支援的功能的登錄值。 這個方法可以將呼叫轉送至適當的表單[SDK 協助程式進行偵錯](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)函式， `SetMetric`。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)