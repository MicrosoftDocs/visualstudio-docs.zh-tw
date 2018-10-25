---
title: IDebugProgramNode2::GetHostPid |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c75fbcbb7a79202fe9e2bf5dec6f6b330fadb8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831246"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得裝載程式的處理序的系統處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetHostPid (   
   AD_PROCESS_ID * pdwHostPid  
);  
```  
  
```csharp  
int GetHostPid (   
   out AD_PROCESS_ID pdwHostPid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwHostPid`  
 [out]傳回裝載處理序的系統處理序識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CProgram`實作的物件[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)介面。  
  
```cpp#  
HRESULT CProgram::GetHostPid(DWORD* pdwHostPid) {    
    // Check for valid argument.    
   if (pdwHostPid)    
    {    
        // Get the process identifier of the calling process.    
      *pdwHostPid = GetCurrentProcessId();    
  
        return S_OK;    
    }    
  
    return E_INVALIDARG;    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

