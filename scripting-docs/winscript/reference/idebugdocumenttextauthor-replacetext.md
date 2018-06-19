---
title: IDebugDocumentTextAuthor::ReplaceText |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa7ef34d035ad89a096414c285b4f66a4f4fa1e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726698"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
取代文件中的文字。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]啟動要取代之字元範圍的位置。  
  
 `cNumToReplace`  
 [in]要取代的字元數。  
  
 `pcharText[]`  
 [in]包含新的字元取代舊的字元緩衝區。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會取代文件中的文字。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentTextAuthor 介面](../../winscript/reference/idebugdocumenttextauthor-interface.md)