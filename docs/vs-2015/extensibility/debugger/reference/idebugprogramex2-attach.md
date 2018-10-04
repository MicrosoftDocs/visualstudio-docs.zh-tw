---
title: IDebugProgramEx2::Attach |Microsoft Docs
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
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1969f8d38cd52572f0d0c7cde603a1ea25c0e0be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490452"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugProgramEx2::Attach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramex2-attach)。  
  
附加至程式的工作階段。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)物件，表示附加的偵錯引擎會傳送至事件的回呼函式。  
  
 `dwReason`  
 [in]值，以從[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)描述在附加作業原因的列舉型別。  
  
 `pSession`  
 [in]值，這個值可唯一識別附加至程式的工作階段。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 此方法應傳回`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`如果已經附加的程式。  
  
## <a name="remarks"></a>備註  
 包含該程式的連接埠可以使用中的值`pSession`來判斷哪一個工作階段嘗試附加至程式。 例如，如果連接埠允許附加至處理序中，一次只能有一個偵錯工作階段，連接埠就可以判斷是否相同的工作階段已附加至處理序中的其他程式。  
  
> [!NOTE]
>  介面傳入`pSession`會僅視為 cookie 值可唯一識別 附加至這個方案的偵錯工作階段管理員提供的介面上的方法沒有任何功能。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)

