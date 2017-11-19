---
title: "IEnumRemoteDebugApplications::Clone |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplications.Clone
apilocation: scrobj.dll
helpviewer_keywords: IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97b135d0139be40fa864064422027e7c3247fc8a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
建立列舉值，包含目前的列舉值的狀態相同。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppessd`  
 [out]列舉值的複本。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立包含目前的列舉值的狀態相同的列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)