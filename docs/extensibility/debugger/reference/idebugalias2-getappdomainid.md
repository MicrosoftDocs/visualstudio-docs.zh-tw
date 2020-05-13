---
title: IDebugAlias2::獲取AppDomainId |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca8f2311b58fc7e73f9eb4f4c14f993c88b9a62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736411"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
檢索應用程式域的標識碼。

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
[出]返回應用程式域識別碼。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 每當重新啟動應用程式並創建新的應用程式域時,應用程式域標識符都會更改。

## <a name="see-also"></a>另請參閱
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
