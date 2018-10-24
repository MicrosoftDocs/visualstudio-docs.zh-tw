---
title: IDebugDisassemblyStream2::GetCodeLocationId |Microsoft Docs
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
ms.openlocfilehash: f3a1cd9cf0035dddc11bfe7c6fa3f3c1b51a083d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932698"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
傳回特定的程式碼內容的程式碼位置識別碼。  
  
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
 [out]傳回的程式碼位置識別碼。 請參閱＜備註＞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_CODE_CONTEXT_OUT_OF_SCOPE`程式碼內容是否有效，但超出範圍。  
  
## <a name="remarks"></a>備註  
 程式碼位置識別碼旨在支援反組譯碼的偵錯引擎 (DE)。 此位置識別碼來追蹤程式碼中的位置所 DE 內部使用，且通常是地址或某種形式的位移。 唯一的需求是，如果程式碼內容的一個位置小於程式碼內容的另一個位置，則對應的程式碼位置識別碼的第一個程式碼內容也必須是小於第二個程式碼內容的程式碼位置識別碼。  
  
 若要擷取的程式碼位置識別碼的程式碼內容，請呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)