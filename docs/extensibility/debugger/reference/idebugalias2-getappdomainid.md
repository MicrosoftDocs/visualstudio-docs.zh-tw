---
title: IDebugAlias2::GetAppDomainId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03d0ebeeddfd212b4ad99b8f1686c4f9d64141d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900252"
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
  
#### <a name="parameters"></a>參數  
 `pappDomainId`  
 [out]傳回應用程式網域識別項。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 建立的應用程式網域識別項的變更時重新啟動應用程式和新的應用程式定義域。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)