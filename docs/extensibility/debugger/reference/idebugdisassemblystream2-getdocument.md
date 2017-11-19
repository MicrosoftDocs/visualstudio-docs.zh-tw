---
title: "IDebugDisassemblyStream2::GetDocument |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetDocument
helpviewer_keywords: IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bbf3ca1c35de6ef8742d5a6dcc5fba4721dc440
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
取得與此輸入資料流相關聯的來源文件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bstrDocumentUrl`  
 [in]文件 URL。  
  
 `ppDocument`  
 [out]傳回[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)物件，代表文件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 有未儲存的實際檔案中的文字文件的偵錯引擎實作這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)