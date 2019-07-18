---
title: IDebugDocumentText::GetContextOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df63362c422289652d45ed4bbc80f117e17fb73c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008713"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
建立文件內容物件，對應至提供的字元位置範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]開始位置的字元位置範圍。  
  
 `cNumChars`  
 [in]範圍中的字元數。  
  
 `ppsc`  
 [out]對應至指定的字元位置範圍文件內容的物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立對應至提供的字元位置範圍的文件內容物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)