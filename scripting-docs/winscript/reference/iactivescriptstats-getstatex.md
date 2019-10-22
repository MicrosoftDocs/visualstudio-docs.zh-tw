---
title: IActiveScriptStats：： GetStatEx |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576116"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
傳回自訂腳本統計資料。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guid`  
 在指定要傳回的統計資料。 與特定 GUID 對應的統計資料的語義完全是定義引擎。  
  
 `pluHi`  
 脫銷64位不帶正負號整數的高32位，表示統計資料。  
  
 `pluLo`  
 脫銷64位不帶正負號整數的低32位，表示統計資料。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未執行方法。|  
  
## <a name="remarks"></a>備註  
 這個方法可讓自訂腳本引擎傳回對自訂主機有意義的統計資料。  
  
> [!NOTE]
> 這個方法目前未執行。  
  
## <a name="see-also"></a>請參閱  
 [IActiveScriptStats：： GetStat](../../winscript/reference/iactivescriptstats-getstat.md)    
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)