---
title: "IDebugDocumentText::GetPositionOfContext |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f843d71096dea4c22eda757a4d6975dfda94180
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
傳回對應至文件內容的字元位置範圍。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `psc`  
 [in]文件內容物件。  
  
 `pcCharacterPosition`  
 [out]開始位置的字元位置範圍。  
  
 `cNumChars`  
 [out]在範圍內的字元數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 提供給這個方法的文件內容必須是與這份文件相關聯。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)