---
title: IRemoteDebugApplication::ResumeFromBreakPoint |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5da5fdbaaf74f463161f1a98bbad7d4d147b418d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729858"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
會繼續執行應用程式目前正在中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>參數  
 `prptFocus`  
 [in]逐步執行模式中，也就是會受到逐步執行模式的執行緒。  
  
 `bra`  
 [in]繼續執行應用程式時要採取動作。  
  
 `era`  
 [in]因為發生錯誤而停止應用程式的情況下所採取的動作。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會繼續應用程式目前正在中斷點。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplication 介面](../../winscript/reference/iremotedebugapplication-interface.md)   
 [BREAKRESUMEACTION 列舉](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列舉](../../winscript/reference/errorresumeaction-enumeration.md)