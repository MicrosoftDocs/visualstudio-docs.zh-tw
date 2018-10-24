---
title: IDebugCodeContext2::GetDocumentContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd0fa6dd8d587ade2ca06c3f39f65fb3a5fd295d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822185"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
取得對應於這個程式碼內容的文件內容。 文件內容代表對應至產生此指令的原始程式碼的原始程式檔中的位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppSrcCxt`  
 [out]傳回[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)對應至程式碼內容的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 一般而言，文件內容可以視為的原始程式檔中的某個位置的程式碼內容時執行資料流中的程式碼指示的位置。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)