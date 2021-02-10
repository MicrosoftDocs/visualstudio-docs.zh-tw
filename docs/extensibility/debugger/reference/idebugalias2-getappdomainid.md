---
title: IDebugAlias2：： GetAppDomainId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c50473e12399e3977de55e67c7251d5783eecfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947121"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
抓取應用程式域的識別碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>參數
`pappDomainId`\
擴展傳回應用程式域識別碼。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 應用程式域識別碼會在應用程式重新開機時變更，並建立新的應用程式域。

## <a name="see-also"></a>另請參閱
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
