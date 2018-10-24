---
title: IDebugProgram2::GetProgramId |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17101ce15fba12a066005dfdb51c7162a6df60d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910032"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
取得此程式的 GUID。  
  
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
 [out]傳回`GUID`此計劃。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 偵錯引擎 (DE) 必須傳回原本傳遞至程式識別碼[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)或是[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 這可讓程式識別在偵錯工具元件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)