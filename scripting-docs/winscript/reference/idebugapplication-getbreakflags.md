---
title: IDebugApplication：： GetBreakFlags |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetBreakFlags
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a614429ebb8cc9271a0444536d14c45b69a9588f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574979"
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
傳回應用程式目前的中斷旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pabf`  
 脫銷應用程式的目前中斷旗標。  
  
 `pprdatSteppingThread`  
 脫銷目前正在執行的執行緒。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回應用程式目前的中斷旗標。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [APPBREAKFLAGS 列舉](../../winscript/reference/appbreakflags-enumeration.md)