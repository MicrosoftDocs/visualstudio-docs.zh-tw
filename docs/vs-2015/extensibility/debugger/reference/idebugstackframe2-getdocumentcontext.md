---
title: IDebugStackFrame2::GetDocumentContext |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc78cf7fc5227d0b0f09ccd27432b784799cb6a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814306"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得此堆疊框架的文件內容。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCxt`  
 [out]傳回[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件，代表來源文件中的目前位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法的速度比呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)方法，然後呼叫[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)方法的程式碼內容。 不過，不保證每個偵錯引擎 (DE) 會實作這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)

