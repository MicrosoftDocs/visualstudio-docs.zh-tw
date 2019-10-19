---
title: IDebugDocumentText：： GetSize |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572089"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
傳回檔中的行數和字元數。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcNumLines`  
 脫銷檔中的行數。 如果此參數為 Null，則方法不會傳回值。  
  
 `pcNumChars`  
 脫銷檔中的字元數。 如果此參數為 Null，則方法不會傳回值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回檔中的行數和字元數。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)