---
title: "IDebugDocumentContext::EnumCodeContexts |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentContext.EnumCodeContexts
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 300102d75fcfa797e8e073b9a1ce77cc5ee2827a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
列舉與此文件內容相關聯的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppescc`  
 [out]程式碼相關聯的內容與此文件內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 文件，通常只有一個程式碼內容，與相關聯的除非文件是 include 檔或範本。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)