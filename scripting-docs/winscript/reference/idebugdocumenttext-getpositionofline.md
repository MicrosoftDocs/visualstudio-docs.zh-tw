---
title: "IDebugDocumentText::GetPositionOfLine |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetPositionOfLine
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0098a78938c745931c529bbc02823d32b8180cde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
傳回對應至該行的第一個字元的字元位置。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cLineNumber`  
 [in]行號。  
  
 `pcCharacterPosition`  
 [out]這一行開頭的文件中的字元位置`cLineNumber`。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回對應至該行的第一個字元的字元位置。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)