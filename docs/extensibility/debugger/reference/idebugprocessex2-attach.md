---
title: IDebugProcessEx2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da89be65f4b02fa0db254dd85463e422d17fe589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
這個方法會通知處理程序工作階段現在偵錯程序。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSession`  
 [in]可唯一識別附加至此處理序的工作階段值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 在傳遞介面`pSession`cookie，可唯一識別附加至此處理序; 的偵錯工作階段管理員值僅被視為是提供的介面上的方法都是的功能。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)