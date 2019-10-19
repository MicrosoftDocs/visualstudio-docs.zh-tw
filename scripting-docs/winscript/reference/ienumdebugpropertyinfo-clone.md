---
title: IEnumDebugPropertyInfo：： Clone |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Clone
ms.assetid: ba6bdfdb-4c12-475c-bafc-efa6c109d7ee
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e5b355d6302d846a8599b697aa9ad0159662cba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574218"
---
# <a name="ienumdebugpropertyinfoclone"></a>IEnumDebugPropertyInfo::Clone
建立枚舉器，其中包含與目前列舉值相同的列舉狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone (  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷傳回復制的 `IEnumDebugPropertyInfo` 介面。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)