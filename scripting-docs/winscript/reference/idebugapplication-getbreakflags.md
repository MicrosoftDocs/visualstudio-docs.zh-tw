---
title: "IDebugApplication::GetBreakFlags |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.GetBreakFlags
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::GetBreakFlags
ms.assetid: 0532ba94-f791-46ad-88ae-5f6ba220b667
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bdccefb3a679694360ed9a7c6fea35eae6bdb1b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetbreakflags"></a>IDebugApplication::GetBreakFlags
傳回目前應用程式的中斷旗標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetBreakFlags(  
   APPBREAKFLAGS*                   pabf,  
   IRemoteDebugApplicationThread**  pprdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pabf`  
 [out]應用程式目前中斷旗標。  
  
 `pprdatSteppingThread`  
 [out]目前執行的執行緒。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回目前應用程式的中斷旗標。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugApplication 介面](../../winscript/reference/idebugapplication-interface.md)   
 [APPBREAKFLAGS 列舉](../../winscript/reference/appbreakflags-enumeration.md)