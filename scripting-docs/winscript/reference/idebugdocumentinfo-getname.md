---
title: "IDebugDocumentInfo::GetName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
傳回指定的文件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dnt`  
 [in]要傳回的文件名稱的類型。  
  
 `pbstrName`  
 [out]包含名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|不知道指定的文件名稱。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回指定的文件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 列舉](../../winscript/reference/documentnametype-enumeration.md)