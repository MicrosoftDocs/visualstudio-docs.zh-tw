---
title: IDebugStackFrame2：： GetDocumentCoNtext |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35ec80a005a3f004de00a12908de38082c405849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164758"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得這個堆疊框架的檔內容。  
  
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
 擴展傳回 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 物件，這個物件表示來源文件中的目前位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法比呼叫 [GetCodeCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 方法更快，然後在程式碼內容上呼叫 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 方法。 但是，不保證每個 debug engine (DE) 將會執行此方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentCoNtext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
