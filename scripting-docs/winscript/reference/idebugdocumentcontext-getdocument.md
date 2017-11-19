---
title: "IDebugDocumentContext::GetDocument |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentContext.GetDocument
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentContext::GetDocument
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776a65ca9adbcf9304e57e0b93f4ebcb4a33bc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontextgetdocument"></a>IDebugDocumentContext::GetDocument
傳回包含此內容的文件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppsd`  
 [out]包含此內容的文件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 `GetDocument`方法會傳回包含此內容的文件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)