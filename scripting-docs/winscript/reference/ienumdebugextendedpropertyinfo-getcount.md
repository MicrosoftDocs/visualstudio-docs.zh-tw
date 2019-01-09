---
title: IEnumDebugExtendedPropertyInfo::GetCount |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::GetCount
ms.assetid: 2c862f62-b57c-4cd4-ac4e-7d372fbda9a4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61a833a2ea8fe9bc09845b369db896b491b65263
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092699"
---
# <a name="ienumdebugextendedpropertyinfogetcount"></a>IEnumDebugExtendedPropertyInfo::GetCount
取得數`ExtendedDebugPropertyInfo`列舉值中的結構。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcelt`  
 [out]傳回的數目`ExtendedDebugPropertyInfo`列舉值中的結構。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumDebugExtendedPropertyInfo 介面](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 結構](../../winscript/reference/extendeddebugpropertyinfo-structure.md)