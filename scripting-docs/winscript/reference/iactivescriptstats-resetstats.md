---
title: IActiveScriptStats::ResetStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd18719cde85b12e9ec5de3b19dbf8e81bd8575
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991998"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
重設此指令碼的統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會重設此指令碼的統計資料。  
  
## <a name="see-also"></a>另請參閱  
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)