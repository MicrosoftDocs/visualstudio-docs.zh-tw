---
title: IDebugDocumentText::GetLineOfPosition |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2512fa3b56a19ed7396c7a351c8d8f8323fff6f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726618"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
傳回指定的字元位置的行號，並選擇性地對應的行內的字元位移。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cCharacterPosition`  
 [in]開始位置的字元位置範圍。  
  
 `pcLineNumber`  
 [out]範圍的行號。  
  
 `pcCharacterOffsetInLine`  
 [in、 out]行內之範圍的字元位移`pcLineNumber`。 如果這個參數是`NULL`，此方法不會傳回值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回至指定的字元位置的行號，並選擇性地對應的行內的字元位移。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText 介面](../../winscript/reference/idebugdocumenttext-interface.md)