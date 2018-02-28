---
title: "IDebugDocumentHost::GetPathName |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42fffa160a1f5b55dc9ba0287c2fdf3073e27e0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
傳回文件的原始程式檔的完整路徑和檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLongName`  
 [out]字串，包含完整名稱。  
  
 `pfIsOriginalFile`  
 [out]旗標，也就是 true，否則`pbstrLongName`否則參考文件，則為 false 的原始檔。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|可以建立或判定來源檔。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回文件的原始程式檔的完整路徑和檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)