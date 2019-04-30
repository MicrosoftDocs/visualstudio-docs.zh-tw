---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f70e8301b6a44397d351345fe3cb8fe0c3d3426e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414036"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
擷取伺服器的易記名稱。

## <a name="syntax"></a>語法

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

#### <a name="parameters"></a>參數
 `pbstrName`

 [out]傳回伺服器的易記名稱。

> [!NOTE]
> 呼叫端負責釋放字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`，否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 若為使用者啟動的伺服器，這個方法所傳回的名稱會是伺服器的完整名稱。 若為自動啟動伺服器，名稱會是該機器的伺服器上執行。

 機器導向名稱時，請呼叫[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)