---
title: IEnumDebugExtendedPropertyInfo::Next |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57cb567926f92c77f52a339fa2fecd7a315bd1b6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893620"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
擷取指定的數目的`ExtendedDebugPropertyInfo`列舉型別序列中的結構。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]數目`ExtendedDebugPropertyInfo`要擷取的結構。  
  
 `rgelt`  
 [out]陣列`ExtendedDebugPropertyInfo`結構擷取。  
  
 `pceltFetched`  
 [out]數目`ExtendedDebugPropertyInfo`實際擷取的結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)