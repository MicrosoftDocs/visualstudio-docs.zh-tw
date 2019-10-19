---
title: IRemoteDebugApplication：： EnumThreads |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumThreads
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ecc2da982e840e059e0d96d2b630190527d43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573841"
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
列舉已知與應用程式相關聯的所有線程。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pperdat`  
 脫銷列舉值，列出已知與應用程式相關聯的所有線程。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會列舉所有已知與應用程式相關聯的執行緒。 可以隨時加入新的執行緒。  
  
## <a name="see-also"></a>請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)