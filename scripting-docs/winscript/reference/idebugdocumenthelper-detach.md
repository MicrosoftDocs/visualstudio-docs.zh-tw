---
title: "IDebugDocumentHelper::Detach |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.Detach
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::Detach
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5abfe1aeba6eb7435e72797f0739c9abc7b5ff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdetach"></a>IDebugDocumentHelper::Detach
這份文件移除文件樹狀目錄中。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將這份文件移除文件樹狀結構。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)