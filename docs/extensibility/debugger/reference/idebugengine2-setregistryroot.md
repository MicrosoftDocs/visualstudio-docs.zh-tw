---
title: IDebugEngine2：： SetRegistryRoot |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730879"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
設定 debug engine (DE) 的登錄根目錄。

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
在要使用的登錄根目錄。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 此方法可讓您 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 指定 DE 應用來取得登錄設定的替代登錄根目錄，例如 "HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp"。

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
