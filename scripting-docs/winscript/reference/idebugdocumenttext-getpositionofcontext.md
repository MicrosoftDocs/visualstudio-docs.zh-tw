---
title: IDebugDocumentText：： GetPositionOfCoNtext |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da759eb98a6cdd28066ddaa8aafe785ede337a6e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572128"
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
傳回對應至檔內容的字元位置範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psc`  
 在檔內容物件。  
  
 `pcCharacterPosition`  
 脫銷字元位置範圍的開始位置。  
  
 `cNumChars`  
 脫銷範圍中的字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 提供給這個方法的檔內容必須與此檔相關聯。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)