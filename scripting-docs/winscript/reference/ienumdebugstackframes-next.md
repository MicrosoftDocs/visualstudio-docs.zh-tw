---
title: "IEnumDebugStackFrames::Next |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e148b5e13bc3d7986451ece11a3a2eada5baa28
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
擷取指定的列舉順序中的區段數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]若要擷取的區段數目。  
  
 `prgdsfd`  
 [out]傳回的陣列`DebugStackFrameDescriptor`介面，表示正在抓取的區段。  
  
 `pceltFetched`  
 [out]實際列舉值所提取的區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取指定的列舉順序中的區段數目。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugStackFrames 介面](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor 結構](../../winscript/reference/debugstackframedescriptor-structure.md)