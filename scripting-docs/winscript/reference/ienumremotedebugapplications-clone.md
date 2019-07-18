---
title: IEnumRemoteDebugApplications::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Clone
ms.assetid: 762f6dac-1be4-49ec-afda-68c1b29f7a4b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06b2eac008b0bccc3d0671e15658b5a189b5dcaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963269"
---
# <a name="ienumremotedebugapplicationsclone"></a>IEnumRemoteDebugApplications::Clone
建立列舉值，包含目前的列舉值相同的狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Clone(  
   IEnumRemoteDebugApplications**  ppessd  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppessd`  
 [out]列舉值的複製品。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會建立包含相同的狀態，為目前的列舉值的列舉值。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumRemoteDebugApplications 介面](../../winscript/reference/ienumremotedebugapplications-interface.md)