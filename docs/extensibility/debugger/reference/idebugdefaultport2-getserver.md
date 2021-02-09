---
title: IDebugDefaultPort2：： Teamfoundationserverfactory.getserver |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e046dbad9329ae377cef6864b7bc71b2ea6a538b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894942"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
這個方法會取得此埠所在伺服器的介面。

## <a name="syntax"></a>語法

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>參數
`ppServer`\
擴展傳回執行 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) 介面的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)是由 Visual Studio 所執行，代表埠所在的伺服器。

## <a name="see-also"></a>另請參閱
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
