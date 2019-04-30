---
title: IDebugDocumentInfo::GetName | Microsoft Docs
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
ms.openlocfilehash: 9975563c27b986190fbd2731c3f36b1e32719c0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970961"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
傳回指定的文件名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dnt`  
 [in]要傳回的文件名稱的型別。  
  
 `pbstrName`  
 [out]包含名稱的字串。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|不知道指定的文件名稱。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回指定的文件名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentInfo 介面](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE 列舉](../../winscript/reference/documentnametype-enumeration.md)