---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17f6e487dee1b5ae490cfc2ab180eb872ed5b5d2
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615103"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
擷取應用程式定義域的識別項。

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
[out]傳回應用程式網域識別項。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 建立的應用程式網域識別項的變更時重新啟動應用程式和新的應用程式定義域。

## <a name="see-also"></a>另請參閱
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)