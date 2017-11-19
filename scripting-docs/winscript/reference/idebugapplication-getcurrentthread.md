---
title: "IDebugApplication::GetCurrentThread |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2240a62b62c917e94f3ace8f516a10f9de66c74d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
傳回目前執行的執行緒相關聯的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pat`  
 [out]與目前執行的執行緒相關聯的執行緒。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回與目前執行的執行緒相關聯的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)