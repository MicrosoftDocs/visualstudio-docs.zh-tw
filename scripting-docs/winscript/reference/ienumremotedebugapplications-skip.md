---
title: IEnumRemoteDebugApplications::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Skip
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5ed991b02394e12f2e3e789b673149c9de18949
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962337"
---
# <a name="ienumremotedebugapplicationsskip"></a>IEnumRemoteDebugApplications::Skip
略過指定的數目的列舉型別序列中的區段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]略過列舉序列中的區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會略過指定的數目的列舉型別序列中的區段。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)