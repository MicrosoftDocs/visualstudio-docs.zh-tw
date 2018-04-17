---
title: IDebugProgramEx2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 440a4ce6b008efe541187d1d99d886f4c7c5f9ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)