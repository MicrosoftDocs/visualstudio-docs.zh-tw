---
title: IDebugDocumentTextExternalAuthor：： GetFileName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c07752d357a261fbc4800c3217a63d3de9489d55
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575981"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
傳回不含路徑資訊的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbstrShortName`  
 脫銷包含檔簡短名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回不含路徑資訊的檔案名稱。 簡短名稱通常用於對話方塊中。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentTextExternalAuthor 介面](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)