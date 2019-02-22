---
title: IActiveScriptStats::GetStat |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0d00c438f0fe03566dfb7efb93645cad02dc7477
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095390"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
傳回其中一個標準的指令碼統計資料。  
  
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
 [in]指定要傳回的統計資料。 值必須為：  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|傳回的陳述式執行，因為指令碼啟動或重設統計資料數目。|  
  
 `pluHi`  
 [out]表示統計資料的 64 位元不帶正負號的整數高 32 位元。  
  
 `pluLo`  
 [out]表示統計資料的 64 位元不帶正負號的整數低 32 位元。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括但不限於下列資料表中的值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回其中一個標準的指令碼統計資料。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)