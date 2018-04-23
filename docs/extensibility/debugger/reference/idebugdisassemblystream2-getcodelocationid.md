---
title: IDebugDisassemblyStream2::GetCodeLocationId |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 86682bb64f041cd8ee1b08bbec02c28492cac7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
傳回特定的程式碼內容的程式碼位置識別項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCodeContext`  
 [in][IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件轉換為識別項。  
  
 `puCodeLocationId`  
 [out]傳回程式碼位置識別項。 請參閱＜備註＞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_CODE_CONTEXT_OUT_OF_SCOPE`的程式碼內容是否有效，但超出範圍。  
  
## <a name="remarks"></a>備註  
 程式碼位置識別項是針對支援反組譯碼的偵錯引擎 (DE)。 此位置識別項供內部 DE 來追蹤程式碼中的位置，且通常是位址或某種類型的位移。 唯一的需求是，如果程式碼內容的一個位置小於另一個位置的程式碼內容則對應的程式碼位置識別碼的第一個程式碼內容也必須是小於第二個程式碼內容的程式碼位置識別項。  
  
 若要擷取的程式碼位置識別項的程式碼內容，請呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)