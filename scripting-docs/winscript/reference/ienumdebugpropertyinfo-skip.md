---
title: IEnumDebugPropertyInfo：： Skip |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574159"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
略過列舉序列中指定數目的 `DebugPropertyInfo` 結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 在要略過的列舉序列中 `DebugPropertyInfo` 結構的數目。  
  
## <a name="return-value"></a>傳回值  
 傳回有效的 `HRESULT`，通常是 `S_OK`。 傳回 `S_FALSE`，並將目前的專案指標設定為列舉的結尾，如果 `celt` 大於列舉值中剩餘的元素數目。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugPropertyInfo 介面](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)