---
title: IDebugDocumentTextExternalAuthor::GetPathName |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727738"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
傳回文件的完整路徑和檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrLongName`  
 [out]包含完整的路徑和檔案名稱的字串。  
  
 `pfIsOriginalFile`  
 [out]布林值，指出是否路徑和檔案名稱，請參閱原始文件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|無法建立或判定的原始程式檔。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回文件的完整路徑和檔案名稱。  
  
 如果`pfIsOriginalFile`是假的路徑和檔案名稱中`pbstrLongName`參照到新建立的暫存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)