---
title: IScriptEntry：： GetRange |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575427"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
傳回專案的開始位置和長度。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pichMin`  
 脫銷對於指定腳本區塊的 `IScriptEntry` 物件，會傳回0。  
  
 對於指定函式物件的 `IScriptEntry` 物件，會傳回目前腳本區塊中函式的開始位置。  
  
 若為 `IScriptScriptlet` 物件，會傳回0。  
  
 `pcch`  
 脫銷針對指定腳本區塊的 `IScriptEntry` 物件，會傳回文字的長度。  
  
 對於指定函式物件的 `IScriptEntry` 物件，會傳回函數定義的長度。  
  
 針對 `IScriptScriptlet` 物件，傳回專案的長度。  
  
## <a name="return-value"></a>傳回值  
 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [IScriptEntry 介面](../../winscript/reference/iscriptentry-interface.md)