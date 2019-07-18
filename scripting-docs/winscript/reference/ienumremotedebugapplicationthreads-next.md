---
title: IEnumRemoteDebugApplicationThreads::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Next
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bde09e2c8372e0bb7e73fabfbd1ad4d9aa6467e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807195"
---
# <a name="ienumremotedebugapplicationthreadsnext"></a>IEnumRemoteDebugApplicationThreads::Next
`Next`方法會擷取指定的數目的列舉型別序列中的區段。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]若要擷取的區段數目。  
  
 `pprdat`  
 [out]傳回的陣列`IRemoteDebugApplicationThread`介面，表示要擷取的區段。  
  
 `pceltFetched`  
 [out]實際的列舉值所擷取的區段數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會擷取指定的數目的列舉型別序列中的區段。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumRemoteDebugApplicationThreads 介面](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)