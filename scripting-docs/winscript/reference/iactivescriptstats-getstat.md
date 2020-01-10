---
title: IActiveScriptStats：： GetStat |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574343"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
傳回其中一個標準腳本統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `stid`  
 在指定要傳回的統計資料。 必須是值：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|傳回自啟動腳本或重設統計資料之後，所執行的語句數目。|  
  
 `pluHi`  
 脫銷64位不帶正負號整數的高32位，表示統計資料。  
  
 `pluLo`  
 脫銷64位不帶正負號整數的低32位，表示統計資料。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括，但不限於下表中的值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回其中一個標準腳本統計資料。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptStats：： GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)