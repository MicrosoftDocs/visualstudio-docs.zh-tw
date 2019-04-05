---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942580"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`如果[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)不應該呼叫方法。 否則會傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是附加程序期間之前[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)呼叫方法。 `OnAttach`方法可以執行 attach 程序本身 (在此情況下，這個方法會傳回`S_FALSE`) 或延遲的附加程序`IDebugEngine2::Attach`方法 (`OnAttach`方法會傳回`S_OK`)。 在可能情況下，`OnAttach`方法可以設定`GUID`要進行偵錯程式的給定`GUID`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
