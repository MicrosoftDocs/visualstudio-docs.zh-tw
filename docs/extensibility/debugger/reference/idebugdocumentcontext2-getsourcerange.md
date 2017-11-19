---
title: "IDebugDocumentContext2::GetSourceRange |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetSourceRange
helpviewer_keywords: IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fc08e761b3944aafd2303bd7266c98dc06e1be8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
取得此文件內容的來源的程式碼範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pBegPosition`  
 [in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)已填入的開始位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。  
  
 `pEndPosition`  
 [in、 out]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)會填入結束位置的結構。 如果不需要這項資訊，請將這個引數為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 來源範圍是從目前的陳述式後面，只要提供程式碼在前一個陳述式之後的原始碼的整個範圍。 來源範圍通常用於混合來源陳述式，包括註解，以在反組譯碼視窗中的程式碼。  
  
 若要取得只要程式碼陳述式包含在此文件內容中的範圍，請呼叫[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)