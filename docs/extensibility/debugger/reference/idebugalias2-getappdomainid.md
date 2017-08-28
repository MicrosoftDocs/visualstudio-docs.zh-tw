---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c168e29ba4884ec10acac89c3cafb74e8d1c77ba
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Retrieves the identifier for the application domain.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameters  
 `pappDomainId`  
 [out] Returns the application domain identifier.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The application domain identifier changes whenever the application is restarted and a new application domain is created.  
  
## <a name="see-also"></a>See Also  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
