---
title: "IDebugDocumentPosition2::IsPositionInDocument |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords: IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc2c5d3a9b4d0a59aa85208479f57490c18d3c2c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
判斷文件位置，是否要包含在指定的文件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDoc`  
 [in][IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)物件，代表包含文件候選項目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法主要用於在中設定中斷點[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。 文件會載入，中斷點位置會呼叫以判斷文件是否包含此位置。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)