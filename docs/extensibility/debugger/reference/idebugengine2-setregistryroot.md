---
title: IDebugEngine2::設置註冊根 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beba304e846126b262c23c0fc8232f79de5fd794
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730879"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
設置調試引擎 (DE) 的註冊錶根。

## <a name="syntax"></a>語法

```cpp
HRESULT SetRegistryRoot( 
   LPCOLESTR pszRegistryRoot
);
```

```csharp
int SetRegistryRoot( 
   string pszRegistryRoot
);
```

## <a name="parameters"></a>參數
`pszRegistryRoot`\
[在]要使用的註冊表根。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法允許[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]指定 DE 應用於獲取註冊表設置的備用註冊表根;例如,「HKEY_LOCAL_MACHINE_SOFTWARE_微軟_VisualStudio_8.0Exp」。。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
