---
title: "IDebugProperty::GetExtendedInfo |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc549ecc4cfa3b3cbbb754585c751b16df2fd8a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
取得擴充屬性的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]陣列`GUID`s 會使多個項目延伸的資訊可以擷取一次。  
  
 `pExtendedInfo`  
 [out]傳回的陣列`VARIANT`，它可以用來擷取的擴充的屬性的資訊。  
  
## <a name="return-value"></a>傳回值  
 傳回有效`HRESULT`，通常`S_OK`。  
  
## <a name="remarks"></a>備註  
 這個介面取得擴充這個物件的資訊。 API 存在的唯一理由擷取本身就無法藉由使用所擷取的資訊`IDebugProperty::GetPropertyInfo`)。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)