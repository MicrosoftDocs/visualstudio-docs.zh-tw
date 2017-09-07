---
title: "IDebugDisassemblyStream2::GetCodeLocationId |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0614509685436f46a2f48eb8b6a6299321f84901
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

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
