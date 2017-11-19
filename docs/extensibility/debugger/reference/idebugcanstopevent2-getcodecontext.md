---
title: "IDebugCanStopEvent2::GetCodeContext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords: IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542003e3a1885a73c2d2ac7198625034930d77b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
取得描述這個事件的位置的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppCodeContext`  
 [out]傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，代表目前的程式碼位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 大部分的執行階段架構的程式碼內容可以視為指向特定指令程式的執行資料流中的地址。  
  
 若要取得的文件內容，也就是行的原始碼導向，呼叫[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)