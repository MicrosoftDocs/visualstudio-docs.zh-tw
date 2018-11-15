---
title: IDebugAlias2::GetAppDomainId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 07c04aff053b8ce304290fefa7f56f08b448f244
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836629"
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