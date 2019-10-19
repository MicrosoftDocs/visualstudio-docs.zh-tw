---
title: IDebugDocumentCoNtext：： EnumCodeCoNtexts |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentContext.EnumCodeContexts
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 790fd55493bfb24b32400bc73ae8a1799a279625
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573484"
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
列舉與此檔內容相關聯的程式碼內容。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppescc`  
 脫銷與此檔內容相關聯的程式碼內容。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 檔通常只會與一個程式碼內容相關聯，除非檔是包含檔案或範本。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentContext 介面](../../winscript/reference/idebugdocumentcontext-interface.md)