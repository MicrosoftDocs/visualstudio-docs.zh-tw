---
title: IDebugCoreServer3：： GetServerFriendlyName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732892"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
抓取伺服器的易記名稱。

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

## <a name="parameters"></a>參數
`pbstrName`\
擴展傳回伺服器的易記名稱。

> [!NOTE]
> 呼叫端負責釋放字串。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若為使用者啟動的伺服器，這個方法所傳回的名稱就是伺服器的完整名稱。 針對自動啟動的伺服器，名稱是伺服器執行所在電腦的名稱。

 若為電腦導向的名稱，請呼叫 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
