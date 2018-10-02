---
title: IDebugProgram2::GetProgramId |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec9805ef49da0331689f34e1657327f2a836b834
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499651"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgram2::GetProgramId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getprogramid)。  
  
取得此程式的 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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

