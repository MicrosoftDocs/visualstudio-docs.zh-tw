---
title: "IRemoteDebugApplication::EnumThreads |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.EnumThreads
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42b57e63716804258ba79ed4e4aceae118cb5f54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
列舉已知為應用程式相關聯的所有執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pperdat`  
 [out]列出所有已知為應用程式相關聯的執行緒的列舉值。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會列舉已知為應用程式相關聯的所有執行緒。 在任何時間，可能會加入新的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)