---
title: "IEnumDebugCodeContexts::Skip |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Skip
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d053fdfe079636755acf125f5a2c02f8690b2a53
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontextsskip"></a>IEnumDebugCodeContexts::Skip
略過指定的數目的列舉順序中的區段。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過將列舉序列中的區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會略過指定的數目的列舉順序中的區段。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugCodeContexts 介面](../../winscript/reference/ienumdebugcodecontexts-interface.md)