---
title: IDebugProgram2::GetProgramId |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5edf51bfa37cfdca7779417cd01320a1ee89cbd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
此程式中取得的 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pguidProgramId`  
 [out]傳回`GUID`此程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 偵錯引擎 (DE) 必須傳回的程式識別項，原先傳遞至[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 這可讓程式的識別到偵錯工具元件。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)