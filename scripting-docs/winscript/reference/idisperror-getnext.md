---
title: "IDispError::GetNext |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cbe4b044f2d3fb1d8ffb08565fc4093fbbe3ec7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
擷取下一個`IDispError`物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppde`  
 [out]下一步指定`IDispError`物件。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取下一個`IDispError`物件。 如果這是上次`IDispError`物件，這個方法會傳回 NULL。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## <a name="see-also"></a>另請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)