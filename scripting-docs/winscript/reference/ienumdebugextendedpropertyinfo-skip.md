---
title: IEnumDebugExtendedPropertyInfo::Skip |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87913f15f8799be0ad3f6616eeea53a8a627e3d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963451"
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
略過指定的數目的`ExtendedDebugPropertyInfo`列舉型別序列中的結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]數目`ExtendedDebugPropertyInfo`略過列舉序列中的結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。 傳回`S_FALSE`並將目前的項目指標設定為列舉結束時，如果`celt`超過列舉值中的剩餘的項目數。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)