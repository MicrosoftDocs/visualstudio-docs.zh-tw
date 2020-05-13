---
title: IDebugCoreServer3::獲取伺服器友好名稱 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732892"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
檢索伺服器的友好名稱。

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
[出]返回伺服器的友好名稱。

> [!NOTE]
> 調用方負責釋放字串。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 對於使用者啟動的伺服器,此方法返回的名稱是伺服器的全名。 對於自動啟動的伺服器,名稱是伺服器運行的計算機的名稱。

 對於面向電腦的名稱,調用[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)方法。

## <a name="see-also"></a>另請參閱
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [取得伺服器名稱](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
