---
title: "IDebugProgramHost2::GetHostName |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostName
helpviewer_keywords: IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17cb56589f9f045b2f478626c47857d5c951494c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
取得標題、 易記名稱或裝載的處理序，此程式的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwType`  
 [in]中的值[GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列舉型別。  
  
 `pbstrHostName`  
 [out]傳回要求的裝載處理序的名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在典型的實作，這個方法，`dwType`參數已忽略，而且會傳回主機電腦的易記名稱。 另一個可能的實作會傳遞`dwType`參數來呼叫[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)方法來取得名稱。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)