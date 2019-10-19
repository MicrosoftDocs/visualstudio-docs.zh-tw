---
title: IDebugDocumentInfo：： GetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570966"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
傳回指定的檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dnt`  
 在要傳回之檔案名稱的類型。  
  
 `pbstrName`  
 脫銷包含名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|指定的檔案名稱未知。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回指定的檔案名稱。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 列舉](../../winscript/reference/documentnametype-enumeration.md)