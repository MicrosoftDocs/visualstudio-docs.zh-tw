---
title: "IActiveScriptStats::GetStat |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
傳回其中一個標準的指令碼統計資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stid`  
 [in]指定要傳回的統計資料。 值必須為：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|傳回執行啟動指令碼或重設統計資料之後的陳述式的數目。|  
  
 `pluHi`  
 [out]表示統計資料的 64 位元不帶正負號的整數高 32 位元。  
  
 `pluLo`  
 [out]表示統計資料的 64 位元不帶正負號的整數低 32 位元。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括但不限於下列資料表中的值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回標準的指令碼統計資料。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)