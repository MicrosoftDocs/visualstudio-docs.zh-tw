---
title: IDebugProperty::GetExtendedInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 707474f786a8f88c0e08d887f2c2b09c8aaedc8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979119"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
取得擴充屬性的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cInfos`  
 [in]擴充的資訊物件的計數。  
  
 `rgguidExtendedInfo`  
 [in]陣列`GUID`s 傳遞，因此可以同時擷取的擴充資訊的多個項目。  
  
 `pExtendedInfo`  
 [out]傳回的陣列`VARIANT`，它可用來擷取擴充的屬性的資訊。  
  
## <a name="return-value"></a>傳回值  
 會傳回有效`HRESULT`，通常是`S_OK`。  
  
## <a name="remarks"></a>備註  
 這個介面取得擴充這個物件的資訊。 API 存在的唯一理由擷取本身就無法使用所擷取的資訊`IDebugProperty::GetPropertyInfo`)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)