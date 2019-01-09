---
title: IDebugDocumentHost::GetPathName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c33844ade2367ffeb7690306a5febbabde2f016
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096027"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
傳回文件的原始程式檔的完整路徑和檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLongName`  
 [out]字串，包含完整的名稱。  
  
 `pfIsOriginalFile`  
 [out]旗標，也就是如果`pbstrLongName`否則參考文件，則為 false 的原始檔。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|沒有原始程式檔就可以建立或決定。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回文件的原始程式檔的完整路徑和檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)