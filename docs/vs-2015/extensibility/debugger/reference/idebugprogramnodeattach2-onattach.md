---
title: IDebugProgramNodeAttach2::OnAttach |Microsoft Docs
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
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73e81537ce73a5b7677174d4694ece16a2a823b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489749"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgramNodeAttach2::OnAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2-onattach)。  
  
將附加至相關聯的程式，或是遵照的附加程序[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>參數  
 `guidProgramId`  
 [in]`GUID`要指派給相關聯的程式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`。 傳回`S_FALSE`如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)不應該呼叫方法。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是附加程序期間之前[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)呼叫方法。 `OnAttach`方法可以執行 attach 程序本身 (在此情況下，這個方法會傳回`S_FALSE`) 或延遲的附加程序`IDebugEngine2::Attach`方法 (`OnAttach`方法會傳回`S_OK`)。 在可能情況下，`OnAttach`方法可以設定`GUID`要進行偵錯程式的給定`GUID`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

