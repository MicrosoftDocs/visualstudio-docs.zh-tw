---
title: IDebugProgramEx2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c58f576a0126472ad60ceeb5fc5289b668bd54dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116044"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
附加至程式的工作階段。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件，表示附加偵錯引擎會傳送事件的回呼函式。  
  
 `dwReason`  
 [in]中的值[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列舉，描述在附加作業的原因。  
  
 `pSession`  
 [in]可唯一識別附加至程式的工作階段值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 此方法應傳回`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`如果已經附加的程式。  
  
## <a name="remarks"></a>備註  
 包含該程式的連接埠可以使用中的值`pSession`來判斷哪一個工作階段嘗試附加至程式。 例如，如果連接埠會允許附加至處理序，一次只能有一個偵錯工作階段，連接埠可以判斷是否相同的工作階段已經附加到處理序中的其他程式。  
  
> [!NOTE]
>  在傳遞介面`pSession`cookie，可唯一識別附加到此程式; 的偵錯工作階段管理員值僅被視為是提供的介面上的方法都是的功能。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)