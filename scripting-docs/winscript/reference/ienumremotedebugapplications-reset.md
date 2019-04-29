---
title: IEnumRemoteDebugApplications::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Reset
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Reset
ms.assetid: a2c03728-999f-400c-bf40-4ced6cd88410
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf00fa40f00e511f56763e6a497ea477bf686d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962271"
---
# <a name="ienumremotedebugapplicationsreset"></a>IEnumRemoteDebugApplications::Reset
將列舉型別序列重設到開頭。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會接受任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會將列舉型別序列重設開頭。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)