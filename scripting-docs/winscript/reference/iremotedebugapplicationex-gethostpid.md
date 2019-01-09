---
title: IRemoteDebugApplicationEx:GetHostPid |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7570abb8436a49fb80f548d1a7136bf0fe7e0814
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091451"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid
傳回主應用程式的處理序識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwHostPid`  
 [out]主機處理序識別項。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|描述|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 使用 IDE。  
  
## <a name="see-also"></a>另請參閱  
 [IRemoteDebugApplicationEx 介面](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)