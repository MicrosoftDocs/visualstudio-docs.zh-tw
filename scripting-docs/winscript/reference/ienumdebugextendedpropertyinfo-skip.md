---
title: "IEnumDebugExtendedPropertyInfo::Skip |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: IEnumDebugExtendedPropertyInfo::Skip
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd7f686ccaa5a3195b82458cf3ee11f02be104f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugextendedpropertyinfoskip"></a>IEnumDebugExtendedPropertyInfo::Skip
略過指定的數目的`ExtendedDebugPropertyInfo`列舉順序中的結構。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]數目`ExtendedDebugPropertyInfo`略過將列舉序列中的結構。  
  
## <a name="return-value"></a>傳回值  
 傳回有效`HRESULT`，通常`S_OK`。 傳回`S_FALSE`，如果目前的項目指標設列舉結尾`celt`大於左項目數目中列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)