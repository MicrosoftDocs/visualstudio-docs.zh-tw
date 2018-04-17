---
title: IDebugEngine2::GetEngineID |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98331e1d81b310d5b3a8da94d9ca78ea48205f3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
取得偵錯引擎 (DE) 的 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pguidEngine`  
 [out]傳回 DE GUID。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 典型的 Guid 的一些範例包括`guidScriptEng`， `guidNativeEng`，或`guidSQLEng`。 新的偵錯引擎會建立自己的 GUID 來識別。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CEngine`實作物件[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面。  
  
```cpp  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)