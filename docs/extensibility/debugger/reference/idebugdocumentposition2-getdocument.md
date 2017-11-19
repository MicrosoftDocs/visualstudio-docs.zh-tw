---
title: "IDebugDocumentPosition2::GetDocument |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2::GetDocument
helpviewer_keywords: IDebugDocumentPosition2::GetDocument
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad743a355e79d455115f31e22f1aef3dbf505992
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentposition2getdocument"></a>IDebugDocumentPosition2::GetDocument
取得包含文件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```csharp  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDoc`  
 [out]傳回[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)物件，表示包含這個位置的文件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)