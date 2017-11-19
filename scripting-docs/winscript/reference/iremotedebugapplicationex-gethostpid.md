---
title: "IRemoteDebugApplicationEx:GetHostPid |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEx:GetHostPid
apilocation: scrobj.dll
helpviewer_keywords: IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ffb5ff1d23c832f5710abf6d97199afe3f777b67
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid
傳回主應用程式的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwHostPid`  
 [out]主機處理序識別項。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 IDE 使用。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationEx 介面](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)