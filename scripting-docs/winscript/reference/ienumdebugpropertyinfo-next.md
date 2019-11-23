---
title: IEnumDebugPropertyInfo：： Next |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574203"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
在列舉序列中，抓取指定數目的 `DebugPropertyInfo` 結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要抓取的 `DebugPropertyInfo`結構數目。  
  
 `rgelt`  
 脫銷已抓取 `DebugPropertyInfo` 結構的陣列。  
  
 `pceltFetched`  
 脫銷傳回實際抓取 `DebugPropertyInfo` 結構的數目。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)